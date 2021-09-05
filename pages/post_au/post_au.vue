<template>
	<view>
		<view class="nav1">
		  <image class="back" src="/static/assets/back.png" mode="widthFix" lazy-load="false" @tap="goback"></image>
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
		<!-- 未认证 -->
		<view class="wrz">
		  <view class="gant">
		    <image src="/static/assets/gant.png" mode="widthFix" lazy-load="false"></image>
		  </view>
		  <span>
		    未认证
		  </span>
		</view>
		<!-- 说明 -->
		<view class="explain">
		  <span>1.请选择需要认证的岗位;</span>
		  <span>2.上传的证书信息，需要和个人基本信息保持一致。</span>
		</view>
		<!-- 认证列表 -->
		<view v-for="(item, index) in rzlist" :key="index" class="rzlist" @click="Jump(index)">
		  <view class="glimg">
		    <image :src="item.Image"  lazy-load="false"></image>
		  </view>
		  <view class="rzxx">
		    <view>{{item.name}}</view>
		    <view>{{item.introduce}}</view>
		  </view>
		  <image class="cuboid" src="../../static/assets/cuboid.png" mode="widthFix" lazy-load="false"></image>
		  <view class="aswitch">{{item.xgdata}}</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				rzlist:[
				  {
				    Image:"../../static/assets/zslogoOne.png",
				    name:"护士认证",
				    introduce:"上传个人从业经历及国家资格证书",
				    xgdata:"待认证"
				  },
				  {
				    Image:"../../static/assets/zslogoTwo.png",
				    name:"护理员认证",
				    introduce:"上传个人从业经历及国家资格证书",
				    xgdata:"待认证"
				  },
				  {
				    Image:"../../static/assets/zslogoThree.png",
				    name:"康复师认证",
				    introduce:"上传个人从业经历及国家资格证书",
				    xgdata:"待认证"  
				  },
				  {
				    Image:"../../static/assets/zslogoFour.png",
				    name:"药剂师认证",
				    introduce:"上传个人从业经历及国家资格证书",
				    xgdata:"待认证"
				  }
				],
				xggdata:""
			}
		},
		methods: {
			Jump(index) {
				console.log(index)
				if(index === 0) {
					uni.navigateTo({
						url:'../nurse_au/nurse_au'
					})
				}
			},
			//返回到上一页
			goback() {
			  wx.navigateTo({
			    url: '../sfrz/sfrz'
			  })
			},
		}
	}
</script>

<style lang="less">
@import "./post_au.less";
</style>
