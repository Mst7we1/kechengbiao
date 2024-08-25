<template>
  <view>
    <image
      v-if="image != null"
      mode="widthFix"
      :src="image"
      class="backimg"
      :style="'height:' + height + 'px'"
    ></image>
    <view v-if="showWeeks" class="weeks" @click="showWeeks = false">
      <view style="background: #ffffff; border-radius: 10rpx">
        <view class="week-top"> 点击查看该周课程表</view>
        <view style="padding: 10rpx">
          <view
            style="display: flex; flex-direction: row"
            v-for="(item, i) in 4"
            :key="i"
          >
            <view
              v-for="(item, j) in 5"
              style=""
              class="week-bt"
              :style="
                5 * i + j + 1 == nowWeek
                  ? 'background: #39b54a; color: white;'
                  : ''
              "
              :key="j"
              @click="changeWeek(5 * i + j + 1)"
            >
              第{{ 5 * i + j + 1 }}周
            </view>
          </view>
        </view>
      </view>
    </view>
    <view>
      <view class="top">
        <view :style="{ height: statusBarHeight + 'px' }"></view>
        <view class="week" @click="changeWeek(0)">
          <view>第{{ nowWeek }}周</view>
          <image
            style="width: 45rpx; height: 45rpx"
            src="../../static/sq-timetable/down.png"
          ></image>
        </view>
        <view style="display: flex; flex-direction: row">
          <view class="top-text" :style="'width:' + (width / 8 - 14) + 'px;'"
            >节</view
          >
          <view
            class="top-text"
            :style="'width:' + (width / 8 + 2) + 'px;'"
            v-for="(item, index) in ['一', '二', '三', '四', '五', '六', '日']"
            :key="index"
          >
            周{{ item }}
          </view>
        </view>
      </view>
      <view
        style="width: 100%; display: flex"
        :style="{ 'padding-top': statusBarHeight + 57 + 'px' }"
      >
        <view>
          <view
            class="left"
            :style="
              'width:' +
              (width / 8 - 14) +
              'px; height: 160rpx; color:' +
              timeColor +
              ';'
            "
            v-for="(item, index) in time.length"
            :key="index"
          >
            <view style="font-size: 30rpx">{{ index + 1 }}</view>
            <view style="font-size: 20rpx">{{ time[index][0] }}</view>
            <view style="font-size: 20rpx">{{ time[index][1] }}</view>
          </view>
        </view>
        <view v-for="(item, index) in time.length" :key="index">
          <view
            v-if="index != 0"
            :style="'margin-top:' + (index == 0 ? 0 : index * 160) + 'rpx;'"
            class="hx"
          >
          </view>
          <view
            v-if="index < 7"
            :style="
              'margin-left:' +
              (index == 0 ? 0 : (index * (width - (width / 8 - 14))) / 7) +
              'px;' +
              'height:' +
              time.length * 160 +
              'rpx;'
            "
            class="sx"
          ></view>
        </view>
        <view
          v-for="(item, index) in courseList"
          v-if="
            (nowWeek >= item.week_begin && nowWeek <= item.week_end) ||
            showNotWeek
          "
          :key="item.id"
        >
          <view
            @click="getCourse(item)"
            class="kcb-item text-center"
            :style="
              'margin-left:' +
              (((item.week - 1) * (width - (width / 8 - 14))) / 7 + 2) +
              'px; margin-top:' +
              ((item.begin - 1) * 160 + 5) +
              'rpx; width:' +
              ((width - (width / 8 - 14)) / 7 - 4) +
              'px; height: ' +
              ((item.end - item.begin + 1) * 151 +
                (item.end - item.begin) * 10) +
              'rpx; ' +
              'background:' +
              (nowWeek >= item.week_begin && nowWeek <= item.week_end
                ? colorArrays[index % 10]
                : '#a0a0a0')
            "
          >
            <view class="smalltext">
              <view style="margin-top: 2px">{{ item.name }}</view>
              <view>{{ item.place }}</view>
              <view>{{ item.teacher }}</view>
              <view>{{ item.begin + "-" + item.end + "节" }}</view>
              <view>
                {{
                  item.week_begin != item.week_end
                    ? item.week_begin + "-" + item.week_end
                    : item.week_begin
                }}周
              </view>
              <view
                v-if="!(nowWeek >= item.week_begin && nowWeek <= item.week_end)"
                >非本周</view
              >
            </view>
          </view>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  name: "SqTimetable",
  emits: ["click"],
  props: {
    showNotWeek: {
      type: Boolean,
      default: true,
    },
    week: {
      type: Number,
      default: 1,
    },
    image: {
      type: String,
      default: null,
    },
    time: {
      type: Array,
      default: function () {
        return [
         ["8:30", ""],
         ["", "10:10"],
         ["10:20", ""],
         ["", "12:00"],
         ["13:30", ""],
         ["", "15:10"],
         ["15:20", ""],
         ["", "17:00"],
         ["17:40", ""],
         ["", "19:20"],
         ["19:30", ""],
         ["", "21:10"],
        ];
      },
    },
    colorArrays: {
      type: Array,
      default: function () {
        return [
          "#70eb55",
          "#ffc450",
          "#ff9bd7",
          "#86affe",
          "#58eea4",
          "#ffa17d",
          "#1cbbb4",
          "#6964ad",
          "#d42245",
          "#218285",
        ];
      },
    },
    timeColor: {
      type: String,
      default: "#000000",
    },
    courseList: {
      type: Array,
      default: function () {
        return [];
      },
    },
  },
  data() {
    return {
      width: uni.getSystemInfoSync().windowWidth,
      height: uni.getSystemInfoSync().windowHeight,
      statusBarHeight: uni.getSystemInfoSync().statusBarHeight,
      showWeeks: false,
      nowWeek: this.week,
    };
  },
  methods: {
    getCourse(item) {
      this.$emit("click", item);
    },
    changeWeek(week) {
      let that = this;
      if (week) {
        that.showWeeks = false;
        that.nowWeek = week;
      } else {
        that.showWeeks = true;
      }
    },
  },
};
</script>

<style>
.kcb-item {
  position: absolute;
  justify-content: center;
  display: flex;
  border-radius: 5px;
  background-size: 400% 400%;
  animation: Change 2s ease infinite;
}

.hx {
  position: absolute;
  display: flex;
  border-bottom: 1px dashed #a3a3a3;
  left: 0;
  right: 0;
}

.sx {
  position: absolute;
  display: flex;
  /* border-left: 1px dashed #a3a3a3; */
}

.smalltext {
  display: block;
  color: #fff;
  font-size: 24rpx;
  font-weight: bolder;
  overflow: hidden;
  text-overflow: ellipsis;
}

.left {
  justify-content: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  color: black;
}

.text-center {
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
}

.top {
  display: flex;
  flex-direction: column;
  color: black;
  align-items: center;
  position: fixed;
  background: #fff;
  z-index: 1;
  border-bottom: 1rpx solid #a3a3a3;
  font-size: 30rpx;
}

.top-text {
  justify-content: center;
  display: flex;
  align-items: center;
  height: 25px;
}

.backimg {
  width: 100%;
  z-index: -1;
  position: fixed;
}

.week {
  display: flex;
  width: 100%;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  padding: 1rpx;
  height: 30px;
}

.weeks {
  width: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  z-index: 2;
}

.week-top {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #39b54a;
  color: #ffffff;
  padding: 25rpx 0;
  border-radius: 10rpx 10rpx 0 0;
}

.week-bt {
  display: flex;
  background: #f0f0f0;
  margin: 5rpx;
  padding: 8rpx 5rpx;
  width: 120rpx;
  align-items: center;
  justify-content: center;
  border-radius: 5rpx;
  font-size: 25rpx;
}
</style>
