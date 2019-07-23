<template>
    <div class="screen-page">
        <!-- 标题 -->
        <div class="screen-head">
            <router-link :to="{path:'index'}">
                <div class="screen-headimg">
                    <img src="../../../static/img/houtui@3x.png" alt="">
                </div>
            </router-link>
            <h5>筛选</h5>
        </div>
        <!-- 筛选部分 -->
        <div class="screen-choosetip">
            <div class="screen-chossetipitems">
                <div class="choosetiptitle">
                    学历要求
                </div>
                <div class="choosetiptype">
                    <template>
                    <span  :class="activeClass == index ? 'active':''" @click="getItem(item,index)"  v-for="(item,index) in chooselist[0].nodes">{{item.name}}</span>
                    </template>
                </div>
            </div>
            <div class="screen-chossetipitems">
                <div class="choosetiptitle">
                    薪资待遇
                </div>
                <div class="choosetiptype">
                    <template>
                    <span :class="activeClass1 == index ? 'active':''" @click="getItem1(item,index)"  v-for="(item,index) in chooselist[1].nodes">{{item.name}}</span>
                    </template>
                </div>
            </div>
            <div class="screen-chossetipitems">
                <div class="choosetiptitle">
                    经验要求
                </div>
                <div class="choosetiptype">
                    <template>
                    <span :key="index"  :class="activeClass2 == index ? 'active':''" @click="getItem2(item,index)"  v-for="(item,index) in chooselist[2].nodes">{{item.name}}</span>
                    </template>
                </div>
            </div>
            <div class="screen-chossetipitems">
                <div class="choosetiptitle">
                    行业分类
                </div>
                <div class="choosetiptype">
                    <template>
                    <span :key="index"  :class="activeClass3 == index ? 'active':''" @click="getItem3(item,index)"  v-for="(item,index) in chooselist[3].nodes">{{item.name}}</span>
                    </template>
                </div>
            </div>
          
        </div>
        <!-- 尾部 -->
        <div class="screen-subbtn">
            <span>

            </span>
            <span>
                
            </span>
        </div>
        <div class="screen-footer" style="min-height: 50px;">

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
            isActive:true,
            activeClass: 0,
            activeClass1: 0,
            activeClass2: 0,
            activeClass3: 0,
            choose:"",
            choose1:"",
            choose2:"",
            choose3:"",
            chooselist:[
                {
                    nodes:[
                        {
                            "id": 1,
                            "name": "全部",
                        },
                        {
                            "id": 2,
                            "name": "初中及以下",
                        }, {
                            "id": 3,
                            "name": "中专/中技",
                        },
                        {
                            "id": 4,
                            "name": "高中",
                        },{
                            "id": 5,
                            "name": "大专",
                        },{
                            "id": 6,
                            "name": "本科",
                        },{
                            "id": 7,
                            "name": "硕士",
                        },{
                            "id": 8,
                            "name": "博士",
                        }
                    ] 
                },
                {
                    nodes:[
                        {
                            "id": 1,
                            "name": "全部",
                        },
                        {
                            "id": 2,
                            "name": "3K以下",
                        }, {
                            "id":3,
                            "name": "3-5K",
                        },
                        {
                            "id": 4,
                            "name": "5-10K",
                        },{
                            "id": 5,
                            "name": "10-20K",
                        },{
                            "id": 6,
                            "name": "20-50K",
                        },{
                            "id": 7,
                            "name": "50K以上",
                        }
                    ]
                }, {
                    nodes:[
                        {
                            "id": 1,
                            "name": "全部",
                        },
                        {
                            "id": 2,
                            "name": "在校生",
                        }, {
                            "id":3,
                            "name": "应届生",
                        },
                        {
                            "id": 4,
                            "name": "1年以内",
                        },{
                            "id": 5,
                            "name": "1-3年",
                        },{
                            "id": 6,
                            "name": "3-5年",
                        },{
                            "id": 7,
                            "name": "5-10年",
                        },{
                            "id": 8,
                            "name": "10年以上",
                        }
                    ]
                },{
                    nodes:[
                        {
                            "id": 1,
                            "name": "全部",
                        },
                        {
                            "id": 2,
                            "name": "电子商务",
                        }, {
                            "id":3,
                            "name": "游戏",
                        },
                        {
                            "id": 4,
                            "name": "媒体",
                        },{
                            "id": 5,
                            "name": "广告营销",
                        },{
                            "id": 6,
                            "name": "数据服务",
                        },{
                            "id": 7,
                            "name": "医疗健康",
                        },{
                            "id": 8,
                            "name": "生活服务",
                        },{
                            "id": 9,
                            "name": "O2O",
                        }
                    ]
                }
            ],
            nodes:[
                    {
                        "id": 1,
                        "name": "页面展示",
                    },
                    {
                        "id": 2,
                        "name": "产品问题",
                    }, {
                        "id": 3,
                        "name": "操作问题",
                    },
                ]
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
        },
        // change(){
        //     this.isActive = !this.isActive;
        //         if (this.isActive == true) {
        //             this.activeDisplay = 'block';
        //         } else {
        //             this.activeDisplay = 'none';
        //         }
        // },
        getItem(item,index){
            this.activeClass = index;  // 把当前点击元素的index，赋值给activeClass
            this.choose = item.id
            console.log(this.choose)
        },
        getItem1(item,index){
            this.activeClass1 = index;  // 把当前点击元素的index，赋值给activeClass
            this.choose1 = item.id
            console.log(this.choose1)
        },
        getItem2(item,index){
            this.activeClass2 = index;  // 把当前点击元素的index，赋值给activeClass
            this.choose2 = item.id
            console.log(this.choose2)
        },
        getItem3(item,index){
            this.activeClass3 = index;  // 把当前点击元素的index，赋值给activeClass
            this.choose3 = item.id
            console.log(this.choose3)
        },
    },

}
</script>


<style scoped>

/* .change{
    background: #FFFFFF;
    border: 1px solid #3486F7;
    border-radius: 5px;
} */


</style>