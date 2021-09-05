<template>
	<view  style="overflow: hidden;">
	<!--pages/my/my.wxml-->
	<image class="banner" src="/static/assets/mybanner.png" mode="widthFix" :lazy-load="true"></image>
	<!-- 顶部信息 -->
	<view class="top">
	  <view class="title">
	    个人中心
	  </view>
	  <view class="headpic">
	    <image mode="widthFix" src="/static/assets/touxiang.png" :lazy-load="true"></image>
	  </view>
	
	  <view class="profile">
	    <view class="name">王小蒙</view>
	    <view class="id">
	      ID:95279527
	    </view>
	  </view>
	  <view class="verifyed">
	    已认证
	  </view>
	
	</view>
	<!-- 护士认证信息 -->
	<view class="verify">
	  <image class="verifybanner" src="/static/assets/verifybanner1.png" mode="widthFix"></image>
	  <view class="left">
	    小护来了平台认证
	  </view>
	  <view class="right">
	    <image class="duihao" src="/static/assets/duihao.png" mode="widthFix"></image>
	    王小蒙-高级护士
	  </view>
	</view>
	<!-- 提现信息 -->
	<view class="cash">
	  <image class="cashbanner" mode="widthFix" src="/static/assets/moneybanner.png"></image>
	  <view class="row-a1">
	    <view class="ablecash">
	      <view style="margin-top:15rpx">
	        可提现￥
	      </view>
	
	      <view class="ligh">2689</view>
	    </view>
	    <view class="cashbtn">
	      <button size="mini" type="default" hover-start-time="20">立即提现
	      </button>
	    </view>
	  </view>
	  <view class="row-a2" @tap="towaitclose">
	    <view class="line">
	
	    </view>
	    <view class="left">
	      <view class="title">
	        订单待结算
	      </view>
	      <view class="total">
	        283
	      </view>
	
	    </view>
	    <view class="right">
	      <view class="title">
	        总收益(元)
	      </view>
	      <view class="total">
	        6879.3
	      </view>
	    </view>
	  </view>
	  <view class="row-a3">
	    申请提现，预计2小时即可到账
	  </view>
	
	</view>
	<!-- 功能模块 -->
	<view class="btns">
	
	  <view class="msg item">
	    <view class="flexbox">
	      <image class="pic" src="/static/assets/message.png" mode="widthFix"></image>
	      <view class="text">
	        我的消息
	        <span style="margin-left:7rpx;color:#999">(2)</span>
	      </view>
	    </view>
	
	    <image class="go" src="/static/assets/arrow.png" mode="widthFix"></image>
	  </view>
	  <view class="zgrz item" @click="tozgrz()">
	    <view class="flexbox">
	      <image class="pic" src="/static/assets/zgrz.png" mode="widthFix" :lazy-load="true"></image>
	      <view class="text">
	        资格认证
	      </view>
	    </view>
	
	    <image class="go" src="/static/assets/arrow.png" mode="widthFix"></image>
	  </view>
	  <view class="lxkf item">
	    <view class="flexbox">
	      <image class="pic" src="/static/assets/lxkf.png" mode="widthFix"></image>
	      <view class="text">
	        联系客服
	      </view>
	    </view>
	
	    <image class="go" src="/static/assets/arrow.png" mode="widthFix"></image>
	  </view>
	  <view class="ckgg item">
	    <view class="flexbox">
	      <image class="pic" src="/static/assets/ckgg.png" mode="widthFix"></image>
	      <view class="text">
	        查看公告
	      </view>
	    </view>
	
	    <image class="go" src="/static/assets/arrow.png" mode="widthFix"></image>
	  </view>
	</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			towaitclose() {
			  wx.navigateTo({
			    url: "/pages/waitclose/waitclose",
			    success: (result) => {},
			    fail: () => {},
			    complete: () => {}
			  })
			},
			tozgrz() {
			  uni.navigateTo({
			    url: "/pages/zgrz/zgrz",
			  })
			},
		}
	}
</script>

<style lang="less">
@import "./my.less";
</style>
