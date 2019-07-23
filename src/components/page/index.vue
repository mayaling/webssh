<template>
	<div class="index-page">
		<div class="index-head-box">
			<div class="index-head">
				<h5>工作</h5>
				

				<div class="indexheadimg">
						<router-link :to="{path:'publish'}">
								<img src="../../../static/img/jiahao.png" alt="">
				
							</router-link>
				</div>
			</div>
		</div>
		<div class="index-banner">
			<ul class="tabchange">
				<!-- <router-link :to="{path:'addproduct'}"><li>推荐</li></router-link>
				<router-link :to="{path:'addproduct'}">	<li>最新</li></router-link> -->
				<!-- <li><router-link :to="{path:'addproduct'}">推荐</router-link></li> -->
				<li class="selected">推荐</li>
				<li><router-link :to="{path:'new'}">最新</router-link></li>
			</ul>
			<ul class="shaixuan">
				<router-link :to="{path:'location'}">
					<li>
						<span>地区</span>
						<span>
							<img src="../../../static/img/Rectangle 4 Copy.png" alt="">
						</span>
					</li>
				</router-link>
				<router-link :to="{path:'positiontype'}">
					<li class="positiontype">
						<span>筛选</span>
						<span>
							<img src="../../../static/img/Rectangle 4 Copy.png" alt="">
						</span>
					</li>
				</router-link>
			</ul>
		</div>
		<div class="job">
			<template>
				<router-link :to="{path:'jobdetail'}">
					<div class="joblist">
						<div class="joblisttop">
							<!-- <div class="joblisticon">
								<img src="./imgs/Group 25@3x.png" alt="">
							</div> -->
							<div class="joblistinner">
								<p class="joblistname">
									<span class="jobname">西点师</span>
									<!-- <span class="nametip">高通过率</span> -->
								</p>
								<span class="jobtitle">上海满汉全席餐饮</span>
								<div class="slogan">
									<div class="nametip">
										<span >上海 宝山区 顾村</span>
										<span>经验不限</span>
										<span>大专</span>
									</div>
									<!-- <span class="nametip">上海 宝山区 顾村</span>
									<span class="nametip">经验不限</span>
									<span class="nametip">大专</span> -->
								</div>
							</div>
							<div class="jobprice">
								<span>12-18K</span>
							</div>
							<div class="jolist-bottom">
								<div class="joblist-logo">
									<img src="../../assets/mine_01.png" alt="">
								</div>
								<div class="joblist-desc">
									大佬
								</div>
								<div class="joblist-time">
									06月09日
								</div>
							</div>
						</div>
						<!-- <div class="joblistbottom">
							<div class="joblistbottom-price">
								<p>123</p>
								<span>借款范围(元)</span>
							</div>
							<div class="joblistbottom-date">
								<p>123天</p>
								<span>放款时间</span>
							</div>
							<div class="joblistbottom-radio">
								<p>123</p>
								<span>日利率</span>
							</div>
						</div> -->
					</div>
				</router-link>
			</template>
		</div>

		

		<!-- <el-form :model="ruleForm"  ref="ruleForm" class="index-form">
			<el-form-item prop="name">
				<div class="indexinput-item">
					<span>联系人</span>
				<input type="text" v-model.trim="form.name">
				</div>
			</el-form-item>
			<el-form-item prop="email">
				<div class="indexinput-item">
						<span>邮箱</span>
					<input type="text" v-model.trim="form.email">
				</div>
			</el-form-item>
			<el-form-item prop="produce">
					<div class="indexinput-produce">
						<textarea  style="background:#F2F3F7; height:7.56rem;width:calc(100% - 1.5rem);margin-left:0.75rem;margin-top:0.75rem; border: none;outline: none;" placeholder="请简单介绍下自己" v-model.trim="form.produce"></textarea >
						<p>0/200</p>  
					</div>
				</el-form-item>
		</el-form> -->
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
		sendindex(){
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