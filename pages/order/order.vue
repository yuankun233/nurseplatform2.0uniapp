<template>

	<view class="container666">
		<!--pages/order/order.wxml-->
		<!-- 标题 -->
		<view class="title">
			订单
		</view>

		<view>
			<view>
				<u-tabs-swiper ref="uTabs" :list="list" :current="current" @change="tabsChange" :is-scroll="false"
					:bold="false" swiperWidth="750" inactive-color="#707070" active-color="#3488F8"
					:bar-style="{backgroundColor:'#3488F8'}"></u-tabs-swiper>
			</view>
			<swiper :current="swiperCurrent" @transition="transition" @animationfinish="animationfinish">
				<swiper-item class="swiper-item">
					<scroll-view scroll-y style="width: 100%;">
						<view class="swiper-div content1">
							<view v-for="(item, index) in tabs" :key="index" class="item" @click.stop="goOrderDetail">
								<view class="row-a1">
									<view class="name">{{item.name}}</view>
									<view class="status">
										待服务
									</view>
								</view>
								<view class="row-a2">
									<view class="serve">
										{{item.type}}
									</view>
									<view class="hcb">
										{{item.hcb==true?'需要耗材包':'不需要耗材包'}}
									</view>
								</view>
								<view class="row-a3">
									<view class="text">
										<image class="time icon" src="/static/assets/time.png"
											mode="aspectFit|aspectFill|widthFix" lazy-load="false"></image>
										服务时间：
										<view selectable="false" space="false" decode="false"
											style="margin-right:10rpx">
											{{item.servedate}}
										</view>
										{{item.servetime}}
									</view>
									<view class="text">
										<image class="msg icon" src="/static/assets/msg.png"
											mode="aspectFit|aspectFill|widthFix" lazy-load="false"></image>
										情况描述：
										{{item.msg}}

									</view>
									<view class="text">
										<image class="address icon" src="/static/assets/address.png"
											style="width:23rpx;height:29rpx" mode="aspectFit|aspectFill|widthFix"
											lazy-load="false"></image>
										地址：{{item.adress}}
									</view>
									<view class="text">
										<image class="money icon" src="/static/assets/money.png"
											mode="aspectFit|aspectFill|widthFix" lazy-load="false"></image>
										此单可赚
										<view class="light" selectable="false" space="false" decode="false">
											150
										</view>
										元
									</view>

								</view>
								<view class="btns">
									<view class="flexbox">
										<u-button class="calluser" @tap.stop="calluser" :custom-style="customStyle1">
											联系客户
										</u-button>
										<u-button class="go" @tap.stop="go" v-if="btnStatus===0"
											:custom-style="customStyle2">
											出发
										</u-button>
										<u-button class="go" @tap.stop="arrive" v-if="btnStatus===1"
											:custom-style="customStyle2">
											到达
										</u-button>

									</view>

								</view>

							</view>
						</view>
					</scroll-view>
				</swiper-item>
				<swiper-item class="swiper-item">
					<scroll-view scroll-y style="width: 100%;">
						<view class="swiper-div content2">
							<order-message class="order-message">
								<u-button type="default" class="recordBtn">打开录音</u-button>
							</order-message>
						</view>
					</scroll-view>
				</swiper-item>
				<swiper-item class="swiper-item">
					<scroll-view scroll-y style="width: 100%;">
						<view class="swiper-div">
							<order-list></order-list>
						</view>
					</scroll-view>
				</swiper-item>

			</swiper>
		</view>

	</view>

</template>


<script>
	import orderList from '../../components/orderlist/orderlist.vue'
	import orderMessage from '../../components/ordermessage/ordermessage.vue'
	export default {
		data() {
			return {
				//按钮的样式
				customStyle1: {
					width: '140rpx',
					height: '46rpx',
					borderRadius: '10rpx',
					lineHeight: '46rpx',
					fontSize: '23rpx',
					fontFamily: 'PingFang SC'
				},
				customStyle2: {
					width: '140rpx',
					height: '46rpx',
					borderRadius: '10rpx',
					lineHeight: '46rpx',
					fontSize: '23rpx',
					fontFamily: 'PingFang SC',
					backgroundColor: "#3488F8",
					color: '#fff'
				},
				btnStatus: 0, //按钮的状态
				tabs: [{
						title: "待服务",
						status: false,
						name: "张先生",
						type: "静脉采血(单次)",
						hcb: true,
						servedate: "6-11",
						servetime: "13:00-16:00",
						msg: "需要带压脉带以及酒精棉",
						adress: "上海市闵行区",
						money: 150
					},
					{
						title: "服务中",
						status: true,
						name: "李先生",
						type: "陪伴护理",
						hcb: false,
						servedate: "6-12",
						servetime: "15:00-16:00",
						msg: "需要护士跟随",
						adress: "上海市松江区",
						money: 250
					},
					{
						title: "已服务",
						status: false,
						name: "董女士",
						type: "上门服务",
						hcb: false,
						servedate: "6-15",
						servetime: "10:00-16:00",
						msg: "需要带压脉带",
						adress: "上海市浦东新区",
						money: 450
					},
					{
						title: "已服务",
						status: false,
						name: "董女士",
						type: "上门服务",
						hcb: false,
						servedate: "6-15",
						servetime: "10:00-16:00",
						msg: "需要带压脉带",
						adress: "上海市浦东新区",
						money: 450
					},
					{
						title: "已服务",
						status: false,
						name: "董女士",
						type: "上门服务",
						hcb: false,
						servedate: "6-15",
						servetime: "10:00-16:00",
						msg: "需要带压脉带",
						adress: "上海市浦东新区",
						money: 450
					},
					{
						title: "已服务",
						status: false,
						name: "董女士",
						type: "上门服务",
						hcb: false,
						servedate: "6-15",
						servetime: "10:00-16:00",
						msg: "需要带压脉带",
						adress: "上海市浦东新区",
						money: 450
					},
					{
						title: "已服务",
						status: false,
						name: "董女士",
						type: "上门服务",
						hcb: false,
						servedate: "6-15",
						servetime: "10:00-16:00",
						msg: "需要带压脉带",
						adress: "上海市浦东新区",
						money: 450
					},
					{
						title: "已服务",
						status: false,
						name: "董女士",
						type: "上门服务",
						hcb: false,
						servedate: "6-15",
						servetime: "10:00-16:00",
						msg: "需要带压脉带",
						adress: "上海市浦东新区",
						money: 450
					}
				],
				list: [{
						name: '待服务'
					},
					{
						name: '服务中'
					},
					{
						name: '已服务'
					},
				],
				current: 0, // tabs组件的current值，表示当前活动的tab选项
				swiperCurrent: 0, // swiper组件的current值，表示当前那个swiper-item是活动的
			}
		},
		components: {
			orderList,
			orderMessage
		},
		methods: {
			// 跳转至订单详情
			goOrderDetail() {
				uni.navigateTo({
					url: "../orderdetail/orderdetail"
				})
			},
			// 联系客户
			calluser() {
				console.log('联系客户中~~')
			},
			// 出发
			go(e) {
				console.log(e)
				console.log(this.btnStatus)
				this.btnStatus = 1

			},
			// 到达
			arrive() {
				uni.showModal({
					title: "是否确认到达",
					content: "确认到达后将开始服务",
					showCancel: true,
					cancelText: "取消",
					cancelColor: "#000000",
					confirmText: "确定",
					confirmColor: "#3CC51F",
					success: (result) => {
						if (result.confirm) {
							console.log("确认到达")
							// 切换到服务中
							this.current = 1
							this.swiperCurrent = 1
							return
						}

						console.log("取消确认")
					},
					fail: () => {},
					complete: () => {}
				})
			},
			// tabs通知swiper切换
			tabsChange(index) {
				this.swiperCurrent = index;
			},
			// swiper-item左右移动，通知tabs的滑块跟随移动
			transition(e) {
				let dx = e.detail.dx;
				this.$refs.uTabs.setDx(dx);
			},
			// 由于swiper的内部机制问题，快速切换swiper不会触发dx的连续变化，需要在结束时重置状态
			// swiper滑动结束，分别设置tabs和swiper的状态
			animationfinish(e) {
				let current = e.detail.current;
				this.$refs.uTabs.setFinishCurrent(current);
				this.swiperCurrent = current;
				this.current = current;
			},
			// scroll-view到底部加载更多
			onreachBottom() {

			}
		}
	}
</script>
<style lang="less">
	@import "./order.less";

	uni-page-wrapper {
		overflow: hidden !important;
	}

	.container666 {
		background-color: #F1F1F1 !important;
		height: 92.65vh;
	}

	uni-page-wrapper {}

	// swiper组件有默认高度，超出高度会隐藏
	uni-swiper {
		height: 85vh;
		
	}

	// 内容区域
	.swiper-div {
		padding-top: 20rpx;
		height: 85vh;
		overflow-y: auto;//高度与uni-swiper设一致，以便垂直滚动
		padding-bottom: 98rpx;
	}


</style>
