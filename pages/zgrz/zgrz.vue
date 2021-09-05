<template>
	<view>
		<view class="nav">
			<image class="back" src="/static/assets/back.png" mode="widthFix" lazy-load="false" @click="goback"></image>
			<span class="title">资格认证</span>
		</view>
		<!-- 步骤条 -->
		<view class="steps">
			<span style="color:#4178F0">基本信息</span>
			<span style="font-size:40rpx">﹥</span>
			<span>身份认证</span>
			<span style="font-size:40rpx">﹥</span>
			<span>岗位认证</span>
		</view>

		<!-- 表单信息 -->
		<view class="basemsg">
			<u-form :model="form" ref="uForm">
				<u-form-item label="姓名" prop="name">
					<u-input v-model="form.name" />
				</u-form-item>
				<!-- //性别 -->
				<u-form-item label="性别">
					<u-radio-group v-model="form.sex">
						<u-radio v-for="(item, index) in radioList" :key="index" :name="item.sex">
							{{ item.sex }}
						</u-radio>
					</u-radio-group>
				</u-form-item>
				<u-form-item label="出生日期">
					<picker mode="date" :value="date" start="1900-09-01" end="2021-06-23" @change="DateChange">
						<view class="picker">
							{{date}}
						</view>
					</picker>
				</u-form-item>
					<u-form-item label="手机号码" prop="phone" class="phone">
						<u-input v-model="form.phone" />
					</u-form-item>
					<u-form-item label="身份证号码" prop="Id">
						<u-input v-model="form.Id" />
					</u-form-item>
					<u-form-item label="现居地址" prop="site">
						<u-input v-model="form.site" />
					</u-form-item>
					<u-form-item label="服务范围" prop="scope">
						<u-input v-model="form.scope" />
					</u-form-item>
				</u-form>
		</view>
		<!-- 下一步 -->
		<button class="nextbtn" @click="next">
			下一步
		</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				date: '请选择时间', //时间选择
				//性别列表
				radioList: [{
						sex: '女',
						checked: true
					},
					{
						sex: '男',
						checked: false
					}
				],
				form: {
					name: '',//姓名
					phone: '',//手机号
					Id:'',//身份证
					site:'',//现居地址
					scope:'',//服务范围
					sex:''//性别
				},
				rules: {
					name: [{
						required: true,
						message: '请输入姓名',
						// 可以单个或者同时写两个触发验证方式 
						trigger: ['change', 'blur'],
					}],
					phone: [{
						required: true,
						message: '请输入手机号',
						// 可以单个或者同时写两个触发验证方式 
						trigger: ['change', 'blur'],
					}],
					Id: [{
						required: true,
						message: '请输入身份证号码',
						// 可以单个或者同时写两个触发验证方式 
						trigger: ['change', 'blur'],
					}],
					site: [{
						required: true,
						message: '请输入现居地址',
						// 可以单个或者同时写两个触发验证方式 
						trigger: ['change', 'blur'],
					}],
					scope: [{
						required: true,
						message: '请输入服务范围',
						// 可以单个或者同时写两个触发验证方式 
						trigger: ['change', 'blur'],
					}]
				}
			}
		},
		methods: {
			//选择时间赋值
			DateChange(e) {
				this.date = e.target.value
			},
			//跳转到身份认证页面
			next() {
				uni.navigateTo({
					url:'../sfrz/sfrz'
				})
			},
			goback() {
				wx.navigateBack({
					delta: 1,
				})
			}
		},
		onReady() {
			this.$refs.uForm.setRules(this.rules);
		}
	}
</script>

<style lang="less">
	@import "./zgrz.less";
</style>
