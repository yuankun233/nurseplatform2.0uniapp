<template>
<!--components/calender/calender.wxml-->
<view class="calendar">
  <view class="title flex" style=" border-bottom: 1rpx solid #f3f3f3;">
    <view class="flex">
      <view class="icon" @tap="lastMonth">
        上一月
      </view>
      <picker :value="selectDay.year+'-'+selectDay.month" @change="editMonth" mode="date" fields="month" class="year-month">{{selectDay.year}}.{{selectDay.month>9?selectDay.month:"0"+selectDay.month}}
      </picker>
      <view class="icon" @tap="nextMonth">
        下一月
      </view>
    </view>

  </view>

  <!-- 日历头部 -->
  <view class="flex-around calendar-week" style="padding-top:16rpx">
    <view class="view">周日</view>
    <view class="view">周一</view>
    <view class="view">周二</view>
    <view class="view">周三</view>
    <view class="view">周四</view>
    <view class="view">周五</view>
    <view class="view">周六</view>
  </view>

  <!-- 日历主体 -->
  <view class="flex-start flex-wrap calendar-main" :style="'height:' + (dateList.length/7*72) + 'rpx'">
    <view v-for="(item, index) in dateList" :key="index" class="day">
      <view :class="'bg ' + ((item.year === selectDay.year && item.month === selectDay.month) ? (item.day === selectDay.day?'select':''): 'other-month')" @tap.stop="selectChange" :data-day="item.day" :data-year="item.year" :data-month="item.month" :data-date-string="item.dateString">
        {{item.day}}
      </view>
      <view class="spot" v-if="item.spot"></view>
    </view>
  </view>
</view>
</template>


<script>

global['__wxRoute'] = 'components/calender/calender';
// components/calendar/calendar.js
Component({
  /**
   * 组件的属性列表
   */
  properties: {
    spot: {
      type: Array,
      value: []
    },
    defaultTime: {
      type: String,
      value: ""
    }
  },

  /**
   * 组件的初始数据
   */
  data: {
    dateList: [], //日历主体渲染数组
    selectDay: {}, //选中时间
    open: true
  },
  /**
   * 组件的方法列表
   */
  methods: {
    /**
     * 时间戳转化为年 月 日 时 分 秒
     * time: 需要被格式化的时间，可以被new Date()解析即可
     * format：格式化之后返回的格式，年月日时分秒分别为Y, M, D, h, m, s，这个参数不填的话则显示多久前
     */
    formatTime(time, format) {
      function formatNumber(n) {
        n = n.toString()
        return n[1] ? n : "0" + n
      }

      function getDate(time, format) {
        const formateArr = ["Y", "M", "D", "h", "m", "s"]
        const returnArr = []
        const date = new Date(time)
        returnArr.push(date.getFullYear())
        returnArr.push(formatNumber(date.getMonth() + 1))
        returnArr.push(formatNumber(date.getDate()))
        returnArr.push(formatNumber(date.getHours()))
        returnArr.push(formatNumber(date.getMinutes()))
        returnArr.push(formatNumber(date.getSeconds()))
        for (const i in returnArr) {
          format = format.replace(formateArr[i], returnArr[i])
        }
        return format
      }

      function getDateDiff(time) {
        let r = ""
        const ft = new Date(time)
        const nt = new Date()
        const nd = new Date(nt)
        nd.setHours(23)
        nd.setMinutes(59)
        nd.setSeconds(59)
        nd.setMilliseconds(999)
        const d = parseInt((nd - ft) / 86400000)
        switch (true) {
          case d === 0:
            const t = parseInt(nt / 1000) - parseInt(ft / 1000)
            switch (true) {
              case t < 60:
                r = "刚刚"
                break
              case t < 3600:
                r = parseInt(t / 60) + "分钟前"
                break
              default:
                r = parseInt(t / 3600) + "小时前"
            }
            break
          case d === 1:
            r = "昨天"
            break
          case d === 2:
            r = "前天"
            break
          case d > 2 && d < 30:
            r = d + "天前"
            break
          default:
            r = getDate(time, "Y-M-D")
        }
        return r
      }
      if (!format) {
        return getDateDiff(time)
      } else {
        return getDate(time, format)
      }
    },
    //picker设置月份
    editMonth(e) {
      const arr = e.detail.value.split("-")
      const year = parseInt(arr[0])
      const month = parseInt(arr[1])
      this.setMonth(year, month)
    },
    //上月切换按钮点击
    lastMonth() {
      const lastMonth = new Date(
        this.data.selectDay.year,
        this.data.selectDay.month - 2
      )
      const year = lastMonth.getFullYear()
      const month = lastMonth.getMonth() + 1
      this.setMonth(year, month)
    },
    //下月切换按钮点击
    nextMonth() {
      const nextMonth = new Date(
        this.data.selectDay.year,
        this.data.selectDay.month
      )
      const year = nextMonth.getFullYear()
      const month = nextMonth.getMonth() + 1
      this.setMonth(year, month)
    },
    //设置月份
    setMonth(setYear, setMonth, setDay) {
      if (
        this.data.selectDay.year !== setYear ||
        this.data.selectDay.month !== setMonth
      ) {
        const day = Math.min(
          new Date(setYear, setMonth, 0).getDate(),
          this.data.selectDay.day
        )
        const time = new Date(setYear, setMonth - 1, setDay ? setDay : day)
        const data = {
          selectDay: {
            year: setYear,
            month: setMonth,
            day: setDay ? setDay : day,
            dateString: this.formatTime(time, "Y-M-D")
          }
        }
        if (!setDay) {
          data.open = true
        }
        this.setData(data)
        this.dateInit(setYear, setMonth)
        this.setSpot()
        this.triggerEvent("change", this.data.selectDay)
      }
    },
    //展开收起
    openChange() {
      this.setData({
        open: !this.data.open
      })
      this.triggerEvent("aaa", { a: 0 })
      this.dateInit()
      this.setSpot()
    },
    //设置日历底下是否展示小圆点
    setSpot() {
      const timeArr = this.data.spot.map((item) => {
        return this.formatTime(item, "Y-M-D")
      })
      this.data.dateList.forEach((item) => {
        if (timeArr.indexOf(item.dateString) !== -1) {
          item.spot = true
        } else {
          item.spot = false
        }
      })
      this.setData({
        dateList: this.data.dateList
      })
    },
    //日历主体的渲染方法
    dateInit(
      setYear = this.data.selectDay.year,
      setMonth = this.data.selectDay.month
    ) {
      let dateList = [] //需要遍历的日历数组数据
      let now = new Date(setYear, setMonth - 1) //当前月份的1号
      let startWeek = now.getDay() //目标月1号对应的星期
      let dayNum = new Date(setYear, setMonth, 0).getDate() //当前月有多少天
      let forNum = Math.ceil((startWeek + dayNum) / 7) * 7 //当前月跨越的周数
      if (this.data.open) {
        //展开状态，需要渲染完整的月份
        for (let i = 0; i < forNum; i++) {
          const now2 = new Date(now)
          now2.setDate(i - startWeek + 1)
          let obj = {}
          obj = {
            day: now2.getDate(),
            month: now2.getMonth() + 1,
            year: now2.getFullYear(),
            dateString: this.formatTime(now2, "Y-M-D")
          }
          dateList[i] = obj
        }
      } else {
        //非展开状态，只需要渲染当前周
        for (let i = 0; i < 7; i++) {
          const now2 = new Date(now)
          //当前周的7天
          now2.setDate(
            Math.ceil((this.data.selectDay.day + startWeek) / 7) * 7 -
              6 -
              startWeek +
              i
          )
          let obj = {}
          obj = {
            day: now2.getDate(),
            month: now2.getMonth() + 1,
            year: now2.getFullYear(),
            dateString: this.formatTime(now2, "Y-M-D")
          }
          dateList[i] = obj
        }
      }
      this.setData({
        dateList: dateList
      })
    },
    //一天被点击时
    selectChange(e) {
      const year = e.currentTarget.dataset.year
      const month = e.currentTarget.dataset.month
      const day = e.currentTarget.dataset.day
      const dateString = e.currentTarget.dataset.dateString
      const selectDay = {
        year: year,
        month: month,
        day: day,
        dateString: dateString
      }
      if (
        this.data.selectDay.year !== year ||
        this.data.selectDay.month !== month
      ) {
        this.setMonth(year, month, day)
      } else if (this.data.selectDay.day !== day) {
        this.setData({
          selectDay: selectDay
        })
        this.triggerEvent("change", this.data.selectDay)
      }
    }
  },
  lifetimes: {
    attached() {
      let now = this.data.defaultTime
        ? new Date(this.data.defaultTime)
        : new Date()
      let selectDay = {
        year: now.getFullYear(),
        month: now.getMonth() + 1,
        day: now.getDate(),
        dateString: this.formatTime(now, "Y-M-D")
      }
      this.setMonth(selectDay.year, selectDay.month, selectDay.day)
    }
  },
  observers: {
    spot: function (spot) {
      this.setSpot()
    }
  }
})

export default global['__wxComponents']['components/calender/calender'];
</script>
<style>
@import "./calender.css";
</style>