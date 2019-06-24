<template>
  <div >
		<!-- <div class="header">
		<h1 class="title">Refresh & Infinite</h1>
		</div> -->
	
		<scroller
		:on-refresh="refresh"
		:on-infinite="infinite">
		
		<div class="banner">
				<div class="banber-log"></div>
				<div class="boutique" v-for="(item,index) in jingpindata" >
					<div class="boutique-logo">
						<img :src="item.image" alt="">
					</div>
					<span class="boutiquetitle">{{item.name}}</span>
			
					<div class="jingpinlogo">
						<div class="jingpininer">
							精<br/>品
						</div>
					</div>
					<div class="tip">
						最高可借额度（元）
					</div>
					<div class="price">
						{{item.max_price}}
						<!-- 80,000 -->
					</div>
					<!-- <div class="checklimit">
						<a :href="jingpindata.url">查看信用额度</a>
					</div> -->
					<div class="checklimit" @click="gomoney(item,index)" >
						<span >查看信用额度</span>
					</div>
					<div class="tips">
							<div class="tips1">
									<div>
											<span class="tipsimage">
												<img src="../../../static/img/gou@3x.png" alt="">
											</span>
											<span class="tipstitle">循环额度次日可还</span>
										</div>
										<div>
											<span class="tipsimage">
											
											
												<img src="../../../static/img/gou@3x.png" alt="">
											</span>
											<span class="tipstitle">日息最低0.05%</span>
										</div>
								<!-- <ul>
									<li>
										<span class="tipsimage">
											<img src="../../../static/img/gou@3x.png" alt="">
										</span>
										<span class="tipstitle">循环额度 次日可还</span>
									</li>
									<li class="tipafter">
										<span class="tipsimage">
											<img src="../../../static/img/gou@3x.png" alt="">
										</span>
										<span class="tipstitle">日息最低0.05%</span>
									</li>
								</ul> -->
							</div>
							<div class="tips2">
								<div>
									<span class="tipsimage">
										<img src="../../../static/img/gou@3x.png" alt="">
									</span>
									<span class="tipstitle">提前还款无手续费</span>
								</div>
								<div>
									<span class="tipsimage">
										<img src="../../../static/img/gou@3x.png" alt="">
									</span>
									<span class="tipstitle">最高24月分期&nbsp;&nbsp;</span>
								</div>
							</div>
						
					</div>
				</div>
		</div>
		<div class="xianjindai">
			<img src="../../../static/img/Group 14@3x.png" alt="">
		</div>
		<div class="zuixinkouzi">
			<h5>最新口子</h5>
				<div class="kouzi">
					<template v-for="(item , index) in zuixindata">
						<!-- <a :href="item.url"> -->
							<div class="kouzi-item" @click="gomoney(item,index)">
								<p>
									<img :src="item.image" alt="">
									<span>{{item.name}}</span>
								</p>
								<p>{{item.max_price}}</p>
								<p>最高可借（元）</p>
							</div>
						<!-- </a> -->
					</template>
				</div>
			
		</div>
		<!-- <template>
			<div class="zuixinkouzi">
				<h5>最新口子</h5>
				<div class="kouzi1">
					<div class="kouzi-item">
						<p>
							<img src="../../../static/img/Group 25@3x.png" alt="">
							<span>拍手分期</span>
						</p>
						<p>80,000</p>
						<p>最高可借（元）</p>
					</div>
					<div class="kouzi-item">
							<p>
								<img src="../../../static/img/Group 25@3x.png" alt="">
								<span>拍手分期</span>
							</p>
							<p>80,000</p>
							<p>最高可借（元）</p>
						</div>
				</div>
				<div class="kouzi1">
						<div class="kouzi-item">
						<p>
							<img src="../../../static/img/Group 25@3x.png" alt="">
							<span>拍手分期</span>
						</p>
						<p>80,000</p>
						<p>最高可借（元）</p>
					</div>
					<div class="kouzi-item">
							<p>
								<img src="../../../static/img/Group 25@3x.png" alt="">
								<span>拍手分期</span>
							</p>
							<p>80,000</p>
							<p>最高可借（元）</p>
						</div>
				</div>

			</div>
		</template>	 -->
		<!-- <div class="zuixinkouzi" >
			<h5>最新口子</h5>
			<template v-for="(item , index) in zuixindata">
				<el-row type="flex" class="row-bg" justify="space-between">
					<el-col :span="11">
						<div class="kouzi-item">
							<p>
								<img src="../../../static/img/Group 25@3x.png" alt="">
								<span>{{item.name}}</span>
							</p>
							<p>{{item.max_price}}</p>
							<p>最高可借（元）</p>
						</div>
					</el-col>
					<el-col :span="11">
						<div class="kouzi-item">
							<p>
								<img src="../../../static/img/Group 25@3x.png" alt="">
								<span>{{item.name}}</span>
							</p>
							<p>{{item.max_price}}</p>
							<p>最高可借（元）</p>
						</div>
					</el-col>
				</el-row>
			</template>
		</div> -->
		<div class="hot">
			<h5>热门推荐</h5>
			<template v-for="(item , index) in tuijiandata">
				<div class="hotlist">
					<div class="hotlisttop">
						<div class="hotlisticon">
							<img :src="item.image" alt="">
						</div>
						<div class="hostlistinner">
							<p class="hotlistname">
								<span class="hotname">{{item.name}}</span>
								<span class="nametip">高通过率</span></p>
								<span class="hotlisttip">{{item.apply_num}}人已拿到钱</span>
						</div>
						<div class="gomoney" id="item.id" @click="gomoney(item,index)">
							<span>去拿钱</span>
							
						</div>
					</div>
					<div class="hotlistbottom">
						<div class="hotlistbottom-price">
							<p>{{item.max_price}}</p>
							<span>借款金额</span>
						</div>
						<div class="hotlistbottom-date">
							<p>{{item.max_duration}}天</p>
							<span>最高借款期限</span>
						</div>
						<div class="hotlistbottom-radio">
							<p>{{item.rate}}</p>
							<span>日利率</span>
						</div>
					</div>
				</div>
			</template>
		</div>
		<!-- <Tabbar></Tabbar> -->
		<!-- <div class="loadmore">
			<span>点击加载更多</span>
		</div> -->
		<div class="footer" style="min-height: 70px;"></div>
	</scroller>
	
	</div>
</template>

<script>
	import Tabbar from "../common/Tabbar.vue"
	import VueScroller from 'vue-scroller'
    Vue.use(VueScroller)
    export default {
        data: function() {
            return {
				jingpindata:"",
				zuixindata:"",
				tuijiandata:""
            }
        },
        components: {
            Tabbar
        },
        created() {
			this.getjingpin();
			this.getzuixin();
			this.gettuijian();
        },
        computed: {

        },
        methods: {
			getjingpin(){
				var _this = this;
				this.$get('products?per-page=1&sort=sort').then((res) => {
					// console.log(res)
                if (res.code === 1) {
					_this.jingpindata = res.info.items
					// console.log(res)
					// _this.loading = false;
                } else {
                    this.$message.error('数据获取失败');
                }
				}).catch(() => {
					this.loading = false
				})
			},
			getzuixin(){
				var _this = this;
				this.$get('products?type=new&per-page=4').then((res) => {
					// console.log(res)
                if (res.code === 1) {
					_this.zuixindata = res.info.items
					// _this.loading = false;
                } else {
                    this.$message.error('数据获取失败');
                }
				}).catch(() => {
					this.loading = false
				})
			},
			gettuijian(){
				var _this = this;
				this.$get('products?type=1&per-page=10').then((res) => {
                if (res.code === 1) {
					_this.tuijiandata = res.info.items
					// console.log(_this.tuijiandata)
					// _this.loading = false;
                } else {
                    this.$message.error('数据获取失败');
                }
				}).catch(() => {
					this.loading = false
				})
			},
			gomoney(item,index){
				var _this = this;
				console.log(item)
				console.log(index)
				// var url ;
				// this.url = item.url
				console.log(item.name)
				if(!localStorage.getItem("userinfo")){
					this.$router.push("/login")
				}else{
					// _this.user_id = localStorage.getItem("userinfo")
					// console.log(item.id)
					// this.$router.push({path: '/link', query: {user_id:_this.user_id,product_id:item.id,url:item.url}});
					_this.user_id = localStorage.getItem("userinfo")
					this.$router.push({path: '/link', query: {user_id:_this.user_id,product_id:item.id,url:item.url,name:item.name}});

					// this.$post('apply',{user_id:_this.user_id,product_id:item.id}).then((res) => {
					// 	this.$router.push({path: '/link', query: {user_id:_this.user_id,product_id:item.id,url:item.url,name:item.name}});
					// 	// window.location.href = item.url
					// }).catch(() => {
					// 	this.loading = false
					// })
				}
			},
			gomoneyi(){
				var _this = this;
				if(!localStorage.getItem("userinfo")){
					this.$router.push("/login")
				}else{
					_this.user_id = localStorage.getItem("userinfo")
					this.$post('apply',{user_id:_this.user_id?_this.user_id:"",product_id:_this.jingpindata.id}).then((res) => {
						window.location.href = _this.jingpindata.url
					}).catch(() => {
						this.loading = false
					})
				}
				
			},
			refresh (done) {
				setTimeout(() => {
					this.getjingpin();
					this.getzuixin();
					this.gettuijian();
				done()
				}, 1500)
			},
        }
    }
</script>
<style scoped>
  .header {
    position: fixed;
    top: 0;
    left: 0;
    height: 44px;
    width: 100%;
    box-shadow: 0 2px 10px 0 rgba(0,0,0,0.1);
    background-color: #fff;
    z-index: 1000;
    color: #666;
  }
  .header > .title {
    font-size: 16px;
    line-height: 44px;
    text-align: center;
    margin: 0 auto;
  }
</style>