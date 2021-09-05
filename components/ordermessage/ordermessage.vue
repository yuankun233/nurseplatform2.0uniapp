<template>
	<!--components/ordermessage/ordermessage.wxml-->
	<!-- 订单内容 -->
	<view class="order" style="overflow: hidden;">
		<view class="name">
			张先生
		</view>
		<view class="personmsg">
			<view class="sex">男
				<view class="age">35岁</view>
			</view>

			<view class="price">
				<view class="light">
					￥
				</view>
				150
			</view>
		</view>
		<view class="ordernum">
			订单号：6615616654
		</view>
		<view class="type">
			服务项目：静脉采血（单次）需要耗材包
		</view>
		<view class="starttime">
			下单时间:
			<view class="date">
				6-11
			</view>
			13:00-16:00
		</view>
		<view class="servetime">
			服务时间:
			<view class="date">
				6-11
			</view>
			13:00-1 6:00
		</view>
		<view class="address">
			服务地址：上海市闵行区漕宝路333号
		</view>
		<view class="input">
			<view class="dsc">
				情况描述：
			</view>
			<textarea placeholder="客户详细病症，服务内容">

			</textarea>

		</view>
		<slot></slot>
	</view>
</template>


<script>
	global['__wxRoute'] = 'components/ordermessage/ordermessage';
	// components/ordermessage/ordermessage.js
	Component({
		/**
		 * 组件的属性列表
		 */
		properties: {

		},

		/**
		 * 组件的初始数据
		 */
		data: {

		},

		/**
		 * 组件的方法列表
		 */
		methods: {

		}
	})

	export default global['__wxComponents']['components/ordermessage/ordermessage'];
</script>
<style lang="less" scoped>
	@import "./ordermessage.less";
</style>
