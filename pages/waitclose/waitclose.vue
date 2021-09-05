<template>
	<view style="overflow: hidden;">
		<image class="banner" src="/static/assets/daijiesuan.png" mode="widthFix" lazy-load="false"></image>
		<image class="back" src="/static/assets/back.png" mode="widthFix" lazy-load="false" @click="goback()"></image>
		<view class="title">
			待结算
		</view>
		<!-- 顶部区域 -->
		<view class="top">
			<view class="row-a1">
				<view class="left">
					<view class="able">
						可结算金额
						(元)
					</view>
					<view class="price">
						89563.3
					</view>

				</view>
				<view class="right">
					<button size="mini">提现</button>
				</view>
			</view>
			<view class="row-a2">
				<view class="r1">
					<view class="order">
						订单数量
					</view>
					<view class="num">
						369
					</view>
				</view>
				<view class="r1">
					<view class="order">
						昨日新单
					</view>
					<view class="num">
						+7
					</view>
				</view>
				<view class="r1">
					<view class="order">
						昨日收益(元)
					</view>
					<view class="num">
						+352.2
					</view>
				</view>
			</view>
			<view class="indicator">
				<image class="icon" src="/static/assets/promote.png" mode="widthFix"></image>
				<view class="text">
					<view>
						本月接单
					</view>
					<view class="text2">
						已经超过
						<view class="persent">
							89%
						</view>
						同业人员
					</view>

				</view>
				<view class="goorder">
					去接单>
				</view>
			</view>
		</view>

		<!-- 信息统计 -->
		<view class="message">
			<image class="pic2" src="/static/assets/totalprice.png" mode="widthFix" lazy-load="false"></image>
			<image class="pic1" src="/static/assets/totalorder.png" mode="widthFix" lazy-load="false"></image>
			<view class="flexbox">
				<view class="item">
					<image class="icon" src="/static/assets/totalordericon.png" mode="widthFix" lazy-load="false">
					</image>

					<view class="text">
						<view class="tit">
							总订单
						</view>
						<view class="num">
							6932
						</view>
						<view class="time">
							2021.04.06 至今
						</view>
					</view>

				</view>
				<view class="item">
					<image class="icon" src="/static/assets/totalpriceicon.png" mode="widthFix" lazy-load="false">
					</image>

					<view class="text">
						<view class="tit">
							总订单
						</view>
						<view class="num">
							6932
						</view>
						<view class="time">
							2021.04.06 至今
						</view>
					</view>
				</view>
			</view>

		</view>

		<!-- 订单列表 -->
		<!-- <view class="orderlist">
		  <view v-for="(item0, index0) in items" :key="index0" class="item">
		    <view class="date">
		      2021年6月16日
		    </view>
		    <view v-for="(item, index) in item0.orderlist" :key="index" class="checkboxlist"> -->
		<!-- 复选框 -->
		<!-- 	      <view class="flexbox">
		        <view :data-index="index" :data-index0="index0" :class="'checkbox ' + (item.checked?'checkedActive':'')" @click="userCheck()">
		          <image v-if="item.checked" class="checkicon" src="/static/assets/check2.png" mode="widthFix"></image>
		
		        </view>
		        <view class="text">
		          <view class="tit">
		            {{item.title}}
		          </view>
		          <view class="order">
		            订单号：{{item.order}}
		          </view>
		        </view>
		      </view>
		
		      <view class="price">
		        <span style=" font-size: 36rpx">+</span>
		        {{item.price}}
		        <span style=" font-size: 18rpx">元</span>
		      </view>
		    </view>
		
		  </view> -->
		<!-- </view> -->
		<!-- 复选框 -->
		<view class="orderlist">
			<view v-for="(count,index) in 4" :key="index">
				<view class="date">{{data}}</view>
				<view class="checkboxlist" v-for="(item,index) in orderlist" :key="index" :name="item.title">
					<u-checkbox-group @change="checkboxGroupChange">
						<u-checkbox shape="circle" @change="checkboxChange" v-model="item.disabled">
							<view class="text">
								<view class="tit">
									{{item.title}}
								</view>
								<view class="order">
									订单号：{{item.order}}
								</view>
							</view>

						</u-checkbox>
					</u-checkbox-group>
					<view class="price">
						<span style=" font-size: 36rpx">+</span>
						{{item.price}}
						<span style=" font-size: 18rpx">元</span>
					</view>
				</view>
			</view>
		</view>

		<!-- 全选按钮 -->
		<view class="checkbtns">
			<button class="allcheck" @click="checkedAll">
				全选(勾选)
			</button>
			<button class="allclose">
				结算
			</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				data: "2021年6月16日",
				orderlist: [{
						title: "输液港术后护理",
						order: "4009633521453652",
						price: "132.3",
						checked: false,
						disabled: false
					},
					{
						title: "PICC导管术后维护",
						order: "4009633521453652",
						price: "13393.3 ",
						checked: false,
						disabled: false
					}
				],
			}
		},
		methods: {
			// 选中某个复选框时，由checkbox时触发
			checkboxChange(e) {
				//console.log(e);
			},
			// 选中任一checkbox时，由checkbox-group触发
			checkboxGroupChange(e) {
				// console.log(e);
			},
			//全选
			checkedAll() {
				this.orderlist.map(val => {
					val.disabled = !val.disabled;
				})
			},
			goback() {
				wx.navigateBack({
					delta: 1,
				})
			}
		},
	}
</script>
<style lang="less">
	@import "./waitclose.less";
</style>
