<template>
	<view style="overflow: hidden;">
		<!--components/orderlist/orderlist.wxml-->
		<!-- 已服务列表 -->
		<view v-for="(item, index) in tabs" :key="index" class="item" @tap.stop="goOrderDetail">
			<view class="row-a1">
				<view class="name">{{item.name}}</view>
				<!-- <view class="status">
      待服务
    </view> -->
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
					<image class="time icon" src="/static/assets/time.png" mode="aspectFit|aspectFill|widthFix"
						lazy-load="false"></image>
					服务时间：
					<view selectable="false" space="false" decode="false" style="margin-right:10rpx">
						{{item.servedate}}
					</view>
					{{item.servetime}}
				</view>
				<view class="text">
					<image class="msg icon" src="/static/assets/msg.png" mode="aspectFit|aspectFill|widthFix"
						lazy-load="false"></image>
					情况描述：
					{{item.msg}}

				</view>
				<view class="text">
					<image class="address icon" src="/static/assets/address.png" style="width:23rpx;height:29rpx"
						mode="aspectFit|aspectFill|widthFix" lazy-load="false"></image>
					地址：{{item.adress}}
				</view>
				<!-- <view class="text">
      <image
        class="money icon"
        src="../../assets/money.png"
        mode="aspectFit|aspectFill|widthFix"
        lazy-load="false"
        binderror=""
        bindload=""
      />
      此单可赚
      <view
        class="light"
        selectable="false"
        space="false"
        decode="false"
      >
        150
      </view>
      元
    </view> -->

			</view>
			<!-- <view class="btns">
    <view class="flexbox">

    </view>

  </view> -->
			<image class="served" src="/static/assets/served.png" mode="widthFix">

			</image>
		</view>
	</view>
</template>


<script>
	import btns from '../../components/orderlist/btns/btns'
	global['__wxVueOptions'] = {
		components: {
			'btns': btns
		}
	};
	global['__wxRoute'] = 'components/orderlist/orderlist';
	// components/orderlist/orderlist.js
	Component({
		/**
		 * 组件的属性列表
		 */
		properties: {},

		/**
		 * 组件的初始数据
		 */
		data: {

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
					money: 150,
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
					money: 250,
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
					money: 450,
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
					money: 450,
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
					money: 450,
				},
				{
					title: "待服务",
					status: false,
					name: "张先生",
					type: "静脉采血(单次)",
					hcb: true,
					servedate: "6-11",
					servetime: "13:00-16:00",
					msg: "需要带压脉带以及酒精棉",
					adress: "上海市闵行区",
					money: 150,
				},
				{
					title: "待服务",
					status: false,
					name: "张先生",
					type: "静脉采血(单次)",
					hcb: true,
					servedate: "6-11",
					servetime: "13:00-16:00",
					msg: "需要带压脉带以及酒精棉",
					adress: "上海市闵行区",
					money: 150,
				},
				{
					title: "待服务",
					status: false,
					name: "张先生",
					type: "静脉采血(单次)",
					hcb: true,
					servedate: "6-11",
					servetime: "13:00-16:00",
					msg: "需要带压脉带以及酒精棉",
					adress: "上海市闵行区",
					money: 150,
				}
			],
		},

		/**
		 * 组件的方法列表
		 */
		methods: {

		},
	})

	export default global['__wxComponents']['components/orderlist/orderlist'];
</script>
<style lang="less">
	@import "./orderlist.less";
</style>
