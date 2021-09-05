<template>
	<view style="overflow: hidden;">
		<!-- pages/search/search.wxml -->
		<!-- 顶部区域 -->
		<!-- <home-header></home-header> -->
		<!-- 搜索内容 -->
		<!-- <search-content></search-content> -->
		<!-- 日历 -->
		<!-- <search-time></search-time> -->

		<!-- 头部 -->
		<text class="realtit">首页</text>
		<!-- 顶部导航 -->
		<view class="header">
			<!-- 背景图 -->
			<image class="banner" src="/static/assets/banner.png" mode="widthFix" lazy-load="false"></image>
			<view class="top">
				<image class="back" src="/static/assets/back.png" mode="widthFix" lazy-load="false" @tap="back"></image>

				<text class="tit" style="opacity:0">首页</text>
				<view class="nav">
					<!-- 搜索框 -->
					<view class="input" @tap="switchSearch('history')">
						<input class="searchbtn" size="mini" type="default" placeholder="快速搜索">
						<image class="search" src="/static/assets/search.png" mode="widthFix"></image>
					</view>
					<!-- 服务时间 -->
					<view class="servetime" @tap="switchSearch('time')">
						选择服务时间
						<image class="rili" src="/static/assets/rili.png" mode="widthFix"></image>
					</view>

				</view>
			</view>

			<!-- 导航 -->
		</view>
		<!-- 搜索内容 -->
		<view class="content" v-if="searchStatus==='history'">
			<view class="tit">
				搜索历史
			</view>

			<view class="historylist">
				<view v-for="(item, index) in 4" :key="index" class="historyitem">
					静脉采血
				</view>
			</view>
		</view>
		<view class="timesearch" v-if="searchStatus==='time'">
			<view class="tit">
				选择时间
			</view>
			<view class="wrapper">
				<calendar class="calendarUtil"></calendar>
				<view class="timeSelect">
					<view :class="btnStatus==='am'?'btnActive btn':'btn'" @tap="switchBtn('am')">
						上午
						<view class=" time_dur">
							8:00 to 12:00
						</view>

					</view>
					<view :class="btnStatus==='noon'?'btnActive btn':'btn'" @tap="switchBtn('noon')">
						下午
						<view class="time_dur">
							13:00 to 18:00
						</view>
					</view>
					<view :class="btnStatus==='pm'?'btnActive btn':'btn'" @tap="switchBtn('pm')">
						晚上
						<view class="time_dur">
							18:00 to 22:00
						</view>
					</view>
				</view>
				<view class="configAndCancel">
					<view class="cancel" @tap="switchSearch('history')">
						取消
					</view>
					<view class="config" @tap="switchSearch('history')">
						完成
					</view>
				</view>
			</view>

		</view>
	</view>
</template>


<script>
	import calendar from '../../components/calender/calender'
	export default {
		data() {
			return {
				btnStatus: "am", // 默认时间段选择为上午
				searchStatus: 'history' // 搜索模式
			}
		},
		components: {
			calendar
		},
		methods: {
			// 搜索模式切换
			switchSearch(mode) {
				this.searchStatus = mode
			},
			// 时间段选择
			switchBtn(time) {
				this.btnStatus = time
			},
			// 返回首页
			back() {
				uni.navigateBack({
					delta: 1
				})
			}
		},
		onLoad(option) {
			const mode = option.mode
			console.log(mode)
			this.switchSearch(mode) // 初始化切换一次模式
		}
	}
</script>
<style lang="less" scoped>
	@import "./search.less";
</style>
