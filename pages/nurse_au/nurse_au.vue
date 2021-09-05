<template>
	<view>
		<view class="nav1">
		  <image class="back" src="/static/assets/back.png" mode="widthFix" lazy-load="false" @click="goback"></image>
		  <span class="title">资格认证</span>
		</view>
		<!-- 步骤条 -->
		<view class="steps">
		  <span>基本信息</span>
		  <span style="font-size:40rpx">﹥</span>
		  <span>身份认证</span>
		  <span style="font-size:40rpx">﹥</span>
		  <span style="color:#4178F0">岗位认证</span>
		</view>
		<!-- 身份填写 -->
		<view>
		  <view class="data">
		    <view class="zhich">职称</view>
		   <input type="text" placeholder="请输入">
		  </view>
		  <view class="data">
		    <view class="zhich">原工作单位</view>
		   <input type="text" placeholder="请选择输入">
		    <image class="arrows" mode="widthFix" lazy-load="false" src="/static/assets/arrow.png"></image>
		  </view>
		  <view class="data">
		    <view class="zhich">科室</view>
		   <input type="text" placeholder="请输入">
		    <image class="arrows" mode="widthFix" lazy-load="false" src="/static/assets/arrow.png"></image>
		  </view>
		  <view class="data">
		    <view class="zhich">擅长工作</view>
		   <input type="text" placeholder="请输入">
		    <image class="arrows" mode="widthFix" lazy-load="false" src="/static/assets/arrow.png"></image>
		  </view>
		</view>
		<!-- 上传资格证书 -->
		<view>
		  <image class="zgzs" src="/static/assets/zgzs.png" mode="widthFix" lazy-load="false"></image>
		</view>
		<!-- 提交资料 -->
		<button class="nextbtn" @tap="next">
		  提交资料
		</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			goback() {
				wx.navigateBack({
					delta: 1,
				})
			}
		}
	}
</script>

<style>
@import "./nurse_au.css";
</style>
