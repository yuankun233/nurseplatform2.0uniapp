<template>
<!--pages/login/login.wxml-->
<view class="login">
  <image class="login_img_1" mode="aspectFill" src="https://www.xiaohulaile.com/wxcx/logo.png"></image>
  <image class="login_img_2" src="https://www.xiaohulaile.com/wxcx/slogen.png"></image>
  <view class="serve_title">
    小护来了服务端
  </view>

  <view class="login_view">
    <button class="Wx_login" @tap="loginWx">
      <image src="https://www.xiaohulaile.com/wxcx/Wx.png"></image>
      <text>微信用户快捷登录</text>
    </button>
  </view>
  <view class="phone_login" @tap="toLoginPhone">
    <image src="https://www.xiaohulaile.com/wxcx/iphone.png"></image>
    <text>手机号登陆 / 注册</text>
  </view>
  <view @tap="userAgreementC" class="YH_login">
    <text>点击　“注册/登录”　即表示您同意<text class="Text_1">《上海小护来了用户协议》、《服务条款》,</text>
    小护来了向您保证：您的隐私绝不会外泄，请放心注册使用。
    </text>
  </view>
</view>
</template>


<script>

global['__wxRoute'] = 'pages/login/login';
// pages/login/login.js
import { $myRequest } from "../../utils/request" // 引入ajax工具
Page({
  data: {},

  // 微信快捷登录
  loginWx() {
    let p1 = this.wxSilentLogin() // 调用login接口请求code
    let p2 = this.wxGetUserProfile() // 获取用户信息
    Promise.all([p1, p2])
      .then((res) => {
        let code = res[0] // wx.login获取的code
        let iv = res[1].iv // 用户信息
        let encryptedData = res[1].encryptedData // 加密数据
        console.log(code)
        console.log(iv)
        console.log(encryptedData)
        // 向服务器发送登录请求
        try {
        } catch (err) {
          console.log(err)
        }
      })
      .catch((err) => {
        console.log(err)
      })
  },
  // 跳转到手机号登录页面
  toLoginPhone() {
    wx.navigateTo({
      url: "/pages/phone/phone",
      success: (result) => {},
      fail: () => {},
      complete: () => {}
    })
  },
  // 为保证wx.getUserProfile和wx.login的先后顺序,封装成两个promise对象
  wxGetUserProfile: function () {
    return new Promise((resolve, reject) => {
      wx.getUserProfile({
        lang: "zh_CN",
        desc: "用户登录", // 声明获取用户个人信息后的用途，后续会展示在弹窗中，请谨慎填写,不填写无法调用弹窗
        success: (res) => {
          resolve(res)
          // res.encryptedData,
          // res.iv
        },
        // 失败回调
        fail: (err) => {
          reject(err)
        }
      })
    })
  },
  wxSilentLogin: function () {
	  uni.navigateTo({
	  	url:"../home/home"
	  })
    return new Promise((resolve, reject) => {
      wx.login({
        success(res) {
          resolve(res.code)
        },
        fail(err) {
          reject(err)
        }
      })
    })
  }
})

export default global['__wxComponents']['pages/login/login'];
</script>
<style>
@import "./login.css";
</style>