<template>
    <div class="publish-page">
        <!-- 标题 -->
        <div class="publish-head">
            <router-link :to="{path:'index'}">
                <div class="publish-headimg">
                    <img src="../../../static/img/houtui@3x.png" alt="">
                </div>
            </router-link>
            <h5>发布</h5>
        </div>
        <el-form :model="form" ref="form" :rules="rules" class="item-add-list">
            <el-form-item  prop="channel_id">
                <div class="publish-titlebox">
                        <div class="publish-title">
                            <el-collapse v-model="activeNames" @change="handleChange">
                                <el-collapse-item title="公司信息" name="1">
                                    <div>
                                        <el-input v-model="form.companyname" placeholder="请填写"></el-input>
                                    </div>
                                </el-collapse-item>
                            </el-collapse>
                        </div>
                    </div>
            </el-form-item>
            <el-form-item  prop="position">
                <div class="publish-titlebox">
                        <div class="publish-title">
                            <el-collapse @change="handleChange">
                                <el-collapse-item title="职位名称" name="1">
                                    <div>
                                        <el-input v-model="form.positionname" placeholder="请填写"></el-input>
                                    </div>
                                </el-collapse-item>
                                <el-collapse-item title="职位类别" name="2">
                                        <div>
                                            <el-input v-model="form.positiontype" placeholder="请填写"></el-input>
                                        </div>
                                    </el-collapse-item>
                            </el-collapse>
                        </div>
                    </div>
            </el-form-item>
            <el-form-item  prop="location">
                <div class="publish-titlebox">
                        <div class="publish-title">
                            <el-collapse @change="handleChange">
                                <el-collapse-item title="工作地址" name="1">
                                    <div>
                                        <el-input v-model="form.location" placeholder="请填写"></el-input>
                                    </div>
                                </el-collapse-item>
                            </el-collapse>
                        </div>
                    </div>
            </el-form-item>
            <el-form-item  prop="location">
                    <div class="publish-titlebox">
                            <div class="publish-title">
                                <el-collapse @change="handleChange">
                                    <el-collapse-item title="薪资范围" name="1">
                                        <div>
                                            <el-input v-model="form.location" placeholder="请填写"></el-input>
                                        </div>
                                    </el-collapse-item>
                                    <el-collapse-item title="经验要求" name="2">
                                            <div>
                                                <el-input v-model="form.location" placeholder="请填写"></el-input>
                                            </div>
                                        </el-collapse-item>
                                        <el-collapse-item title="最低学历" name="3">
                                                <div>
                                                    <el-input v-model="form.location" placeholder="请填写"></el-input>
                                                </div>
                                            </el-collapse-item>
                                </el-collapse>
                            </div>
                        </div>
                </el-form-item>
                <el-form-item  prop="location">
                        <div class="publish-titlebox">
                                <div class="publish-title">
                                    <el-collapse @change="handleChange">
                                        <el-collapse-item title="职位描述" name="1">
                                            <div class="publishinput-produce">
                                                <textarea  style="background: #F4F4F4; height:7.56rem;width:calc(100% - 1.5rem);margin-left:0.75rem;margin-top:0.75rem; margin-bottom:0.75rem;border: none;outline: none;" 
                                                placeholder="填写详细、清晰的职位描述，有助于您更准确地展开招聘需求例如：1.工作内容… 2.任务要求… 3.特别说明…" v-model.trim="form.produce">
                                                </textarea >
                                            </div>
                                        </el-collapse-item>
                                    </el-collapse>
                                </div>
                            </div>
                    </el-form-item>
        </el-form>
        <div class="publish-positiondescbox">
            <div class="publish-positiondesc">
                <span>发布职位即表示遵守
                    <span class="rule">《犀亿职位信息发布规则》</span>
                    所有职位均有人专人审核，请仔细阅读，如违法规则将可能导致您账号被锁定。
                </span>
            </div>
        </div>
        <div class="publish-loginbtnbox">
            <div class="publish-loginbtn"  @click="login()">
                <span>立即发布</span>
            </div>
        </div>
        <div class="footer" style="min-height: 20px;background:#ffffff;">

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
                produce: '',
                companyname:'',
                positionname:"",
                positiontype:"",
            },
            companyname:"",
            activeNames:"1",
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


<style>
.el-input__inner{
    border: none!important;
}
.el-collapse{
    border:none!important;
}

</style>