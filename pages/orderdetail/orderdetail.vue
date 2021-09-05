<template>
	<view class="container">
		<!--pages/orderdetail/orderdetail.wxml-->
		<!-- 标题 -->
		<image class="back" src="/static/assets/backblack.png" @click="back" mode="widthFix"></image>
		<view class="title">
			订单详情
		</view>
		<!-- 订单详情 -->
		<order-message>

		</order-message>
	</view>
</template>


<script>
	import orderMessage from "../../components/ordermessage/ordermessage.vue"
	export default {
		components: {
			orderMessage
		},
		methods: {
			back() {
				uni.navigateBack({
					delta: 1
				})
			}
		}
	}
</script>
<style>
	@import "./orderdetail.css";
	.container{
		
		background-color: #F1F1F1;
	}
</style>
