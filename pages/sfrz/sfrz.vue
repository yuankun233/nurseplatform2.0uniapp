<template>
	<view>
		<view class="nav">
		  <image class="back" src="/static/assets/back.png" mode="widthFix" lazy-load="false" @tap="goback"></image>
		  <span class="title">资格认证</span>
		</view>
		<!-- 步骤条 -->
		<view class="steps">
		  <span>基本信息</span>
		  <span style="font-size:40rpx">﹥</span>
		  <span style="color:#4178F0">身份认证</span>
		  <span style="font-size:40rpx">﹥</span>
		  <span>岗位认证</span>
		</view>
		<!-- 身份证上传 -->
		<view class="idupload">
		  <view class="tit">
		    请扫描身份证
		  </view>
		  <view class="scanid">
		    <image class="idcard" src="/static/assets/idcard1.png" mode="widthFix" lazy-load="false"></image>
		    <image class="idcard" src="/static/assets/idcard2.png" mode="widthFix" lazy-load="false"></image>
		
		  </view>
		</view>
		<!-- 注意事项 -->
		<view class="warn">
		  <view class="tit">
		    <image src="/static/assets/warn.png" mode="aspectFit|aspectFill|widthFix" lazy-load="false"></image>
		    注意事项
		  </view>
		  <view class="items">
		    <view class="item">
		      <image class="pic" src="/static/assets/standard1.png" mode="aspectFit|aspectFill|widthFix" lazy-load="false"></image>
		      <view class="text">
		        <image class="icon" src="/static/assets/duidui.png" style="width:26rpx;height:18rpx" mode="aspectFit|aspectFill|widthFix" lazy-load="false"></image>
		        <view class="text">
		          标准
		        </view>
		
		      </view>
		    </view>
		    <view class="item">
		      <image class="pic" src="/static/assets/standard2.png" mode="aspectFit|aspectFill|widthFix" lazy-load="false"></image>
		      <view class="text">
		        <image class="icon" src="/static/assets/cuocuo.png" mode="aspectFit|aspectFill|widthFix" lazy-load="false"></image>
		        <view class="text">
		          边框缺失
		        </view>
		
		      </view>
		    </view>
		    <view class="item">
		      <image class="pic" src="/static/assets/standard3.png" mode="aspectFit|aspectFill|widthFix" lazy-load="false"></image>
		      <view class="text">
		        <image class="icon" src="/static/assets/cuocuo.png" mode="aspectFit|aspectFill|widthFix" lazy-load="false"></image>
		        <view class="text">
		          照片模糊
		        </view>
		
		      </view>
		    </view>
		    <view class="item">
		      <image class="pic" src="/static/assets/standard1.png" mode="aspectFit|aspectFill|widthFix" lazy-load="false"></image>
		      <view class="text">
		        <image class="icon" src="/static/assets/cuocuo.png" mode="aspectFit|aspectFill|widthFix" lazy-load="false"></image>
		        <view class="text">
		          闪光强烈
		        </view>
		
		      </view>
		    </view>
		  </view>
		
		</view>
		<!-- 提示信息 -->
		<view class="message">
		  <view class="tit">
		    请上传手持身份证照
		  </view>
		  <view class="text">
		    1.请手持身份证拍照；
		  </view>
		  <view class="text"> 2.请确保照片的内容完整并清晰可见，仅支持jpg、png格式，图 片大小小于5M； </view>
		  <view class="text">3.请上传彩色图像</view>
		</view>
		<!-- 上传手持身份证 -->
		<image class="uploadid" src="/static/assets/uploadid.png" mode="aspectFit|aspectFill|widthFix" lazy-load="false"></image>
		
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
				
			}
		},
		methods: {
			next() {
				uni.navigateTo({
					url:'../post_au/post_au'
				})
			},
			goback() {
			  wx.navigateTo({
			    url: '../zgrz/zgrz'
			  })
			},
		}
	}
</script>

<style lang="less">
@import "./sfrz.less";
</style>
