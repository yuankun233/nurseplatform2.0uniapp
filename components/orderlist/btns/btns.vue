<template>
<!--components/orderlist/btns/btns.wxml-->
<!-- 订单列表按钮 -->
<view class="flex">
  <van-button class="calluser" @tap.stop="calluser">
    联系客户
  </van-button>
  <van-button class="go" @tap.stop="go" v-if="btnStatus===0">
    出发
  </van-button>
  <van-button class="go" @tap.stop="goOrderDetail" v-if="btnStatus===1">
    到达
  </van-button>

</view>
</template>


<script>

global['__wxRoute'] = 'components/orderlist/btns/btns';
// components/orderlist/btns/btns.js
Component({
  /**
   * 组件的属性列表
   */
  properties: {},

  /**
   * 组件的初始数据
   */
  data: {
    btnStatus: 0,
  },

  /**
   * 组件的方法列表
   */
  methods: {
    // 联系客户
    calluser() {
      console.log("联系客户中~~")
    },
    // 跳转到订单详情
    goOrderDetail() {
      // 跳转到订单详情页
      wx.navigateTo({
        url: "/pages/orderdetail/orderdetail",
      })
    },
    // 出发
    go() {
      console.log(this.data.btnStatus)
      this.setData({
        btnStatus: 1,
      })
    },
  },
})

export default global['__wxComponents']['components/orderlist/btns/btns'];
</script>
<style>
@import "./btns.css";
</style>