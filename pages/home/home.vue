<template>
	<view  class="container">
		<!--pages/home/home.wxml-->
		<text class="realtit">首页</text>
		<!-- 顶部导航 -->
		<view class="header">
			<!-- 背景图 -->
			<image class="banner666" src="/static/assets/banner.png" lazy-load="false"></image>
			<view class="top666">
				<text class="tit" style="opacity:0">首页</text>
				<view class="nav666">
					<!-- 搜索框 -->
					<view class="input" @tap.stop="goSearch('history')">
						<button class="searchbtn" size="mini" type="default">快速搜索
						</button>
						<image class="search" src="/static/assets/search.png" mode="widthFix"></image>

					</view>
					<!-- 服务时间 -->
					<view class="servetime" @tap.stop="goSearch('time')">
						选择服务时间
						<image class="rili" src="/static/assets/rili.png" mode="widthFix"></image>
					</view>

				</view>
			</view>

			<!-- 导航 -->
		</view>
		<!--  服务列表 -->
		<view style="padding" class="list">
			<view v-for="(item, index) in 9" :key="index" class="item">
				<view class="left">
					<view class="name">
						张先生
					</view>
					<view class="detail">
						静脉采血(单次)
						<text class="hcb">需要耗材包</text>
					</view>
					<view class="text0" style="margin-bottom:16rpx">
						<image class="icon" src="/static/assets/time.png" mode="aspectFit|aspectFill|widthFix"
							lazy-load="false"></image>
						服务时间：
						<text class="text1">6-11</text>
						13:00-16:00
					</view>
					<view class="text0" style="margin-bottom:16rpx">
						<image class="icon" src="/static/assets/msg.png" mode="aspectFit|aspectFill|widthFix"
							lazy-load="false"></image>
						情况描述：
						<text class="text1">需要带压脉带以及酒精棉</text>

					</view>
					<view class="text0">
						<image class="icon" src="/static/assets/address.png" style="height:30rpx;width:23rpx"
							mode="aspectFit|aspectFill|widthFix" lazy-load="false"></image>
						地址：
						<text class="text1">上海闵行区</text>

					</view>

				</view>
				<view class="right">
					<view class="price">
						<text class="light">￥</text>
						150
					</view>
					<u-button class="gobtn" :ripple='true' @click="show = true">立即抢单</u-button>
					<!-- <van-button class="gobtn" @tap="showModal" data-target="Image">
        立即抢单
      </van-button> -->
				</view>

			</view>

		</view>


		<u-mask :show="show" @click="show = false">
			<view class="warp getsucessbox" @tap.stop>

				<image class="sucesspic" src="/static/assets/getsucess.png" mode="aspectFit|aspectFill|widthFix"
					lazy-load="true"></image>
				<view class="getsucessconte">
					<view class="text">
						恭喜您，抢单成功！
					</view>
					<u-button class="orderdetailBtn" :ripple="true" @click="goDetail()">查看订单</u-button>
					<view class="back" @click="show = false">
						返回首页
					</view>
				</view>


			</view>
		</u-mask>
	</view>
</template>


<script>
	export default {
		data() {
			return {
				show: false
			}
		},
		methods: {
			goSearch(mode) {
				uni.navigateTo({
					url: `../search/search?mode=${mode}`
				})
			},
			goDetail(){
				console.log('跳转详情了')
				// 跳转到详情页
				uni.navigateTo({
					url: `../orderdetail/orderdetail`
				})
				// 同时关闭弹出层
				this.show=false
			}
		}
	}
</script>
<style lang="less">
	@import "./home.less";
	// .container::after {
	// 	content: "";
	// 	position: fixed;
	// 	left: 0;
	// 	bottom: 0rpx;
	// 	width: 100%;
	// 	height: 90rpx;
	// 	z-index: 0;
	// 	box-shadow: 0px -2px 10px 0px rgba(38, 38, 38, 0.1);
	// }
	
</style>
