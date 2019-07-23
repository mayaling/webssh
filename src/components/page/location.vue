<template>
    <div class="jobdetail-page">
        <!-- 标题 -->
        <div class="jobdetail-head">
            <router-link :to="{path:'index'}">
                <div class="jobdetail-headimg">
                    <img src="../../../static/img/houtui@3x.png" alt="">
                </div>
            </router-link>
            <h5>选择地区</h5>
        </div>
       
    </div>
  </template>

<script>
export default {
    data() {
        return {
            form: {
                name: '',
                email: '',
                produce: ''
            },
        }
    },
    created(){

    },
    methods: {
        sendshangwu(){
            var _this = this;
            this.$post('feedback',{user_name:_this.form.name,email:_this.form.email,content:_this.form.produce,type:2}
                ).then((res) => {
                    console.log(res)
                    if(res.code === 1){
                        this.$message({
                            message: '提交成功',
                            type: 'success'
                        });
                        setTimeout(function(){
                            _this.$router.push('/mine');
                        },1000);
                    }else{
                        this.$message.error(res.msg);
                    }
                    this.loading = false
            }).catch(() => {this.loading = false})
        }
    },

}
</script>


<style scoped>


</style>