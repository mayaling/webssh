<template>
        <div class="jobdetail-page">
            <!-- 标题 -->
            <div class="jobdetail-head">
                <router-link :to="{path:'index'}">
                    <div class="jobdetail-headimg">
                        <img src="../../../static/img/houtui@3x.png" alt="">
                    </div>
                </router-link>
                <h5>工作详情</h5>
            </div>
            <!-- titile部分 -->
            <div class="jobdetail-mainhead">
                <div class="mianhead-box">
                    <div class="jobdetail-title">
                        <span class="title">产品经理</span>
                        <span class="price">10K-16K</span>
                    </div>
                    <div class="jobdetail-titletips">
                        <ul>
                            <li>
                                <img src="../../../static/img/Group 9 Copy 2@2x.png" alt="">
                                上海市·静安区
                            </li>
                            <li>
                                <img src="../../../static/img/学历 2@2x.png" alt="">
                                本科
                            </li>
                            <li>
                                <img src="../../../static/img/公文包 2@2x.png" alt="">
                                3-5年
                            </li>
                        </ul>
                    </div>
                   
                </div>
            </div>
            <!-- 描述部分 -->
            <div class="jobdetail-descbox">
                <div class="jobdetai-desc">
                    <p>职位描述</p>
                    <span>有意者可直接电话联系咨询面试！！！
                        【岗位职责:】
                        1.按照餐厅服务质量要求和流程做好餐前准备、餐中服务和餐后收拾工作；
                        2.正确摆台，确保所有餐具、器皿清洁、光亮、无污渍….
                        </span>
                        <span class="lookall">查看全部</span>
                </div>
            </div>

            <!-- 技能部分 -->
            <div class="jobdetial-abilitybox">
                <div class="jobdetial-ability">
                   <p>技能要求</p>
                   <div class="abilitytip">
                        <span >交互</span>
                        <span>网页设计</span>
                        <span>JAVA</span>
                    </div>
                </div>
            </div>
            <!-- 地址 -->
            <div class="jobdetial-addressbox">
                <div class="jobdetial-address">
                    <p> 
                        <img src="../../../static/img/Group 9 Copy 2@2x.png" alt="">
                        上海市静安区昌平路789号
                        <span>
                            <img src="../../../static/img/qianjing@3x.png" alt="">
                        </span>
                    </p>
                </div>
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