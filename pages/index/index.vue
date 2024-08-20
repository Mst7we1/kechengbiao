<template>
  <view>
    <SqTimetable
      :time="time"
      :image="image"
      :timeColor="timeColor"
      :courseList="courseList"
      :showNotWeek="true"
      :week="12"
      @click="getCourse"
    >
    </SqTimetable>
  </view>
</template>

<script>
	
import SqTimetable from "../../components/sq-timetable/sq-timetable.vue";
export default {
  components: {
    SqTimetable,
  },
  data() {
    return {
      time: [
        ["8:20", "9:00"],
        ["9:05", "9:45"],
        ["10:00", "10:40"],
        ["10:45", "11:25"],
        ["11:30", "12:10"],
        ["13:30", "14:10"],
        ["14:15", "14:55"],
        ["15:10", "15:50"],
        ["15:55", "16:35"],
        ["16:40", "17:20"],
        ["18:00", "18:40"],
        ["18:45", "19:25"],
        ["19:40", "20:20"],
        ["20:25", "21:05"],
      ],
      image: null,
      colorArrays: [
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
      ],
      timeColor: "#000000",
      courseList: [
        {
          id: 1000,
          begin: 1,
          end: 2,
          week: 1,
          name: "数据可视化技术与应用",
          week_begin: 1,
          week_end: 16,
          place: "南215",
          teacher: "张娜",
        },
        {
          id: 1001,
          begin: 3,
          end: 4,
          week: 1,
          name: "Linux操作系统管理",
          week_begin: 1,
          week_end: 16,
          place: "南415",
          teacher: "刘晓丹",
        },
        {
          id: 1003,
          begin: 7,
          end: 8,
          week: 1,
          name: "数据采集与预处理",
          week_begin: 1,
          week_end: 16,
          place: "西306",
          teacher: "王磊",
        },
        {
          id: 1004,
          begin: 1,
          end: 2,
          week: 2,
          name: "Scala编程基础",
          week_begin: 1,
          week_end: 16,
          place: "南610",
          teacher: "赵阳",
        },
        {
          id: 1005,
          begin: 5,
          end: 6,
          week: 2,
          name: "美育",
          week_begin: 1,
          week_end: 16,
          place: "美育实训室1（小白楼二楼）",
          teacher: "曹洋",
        },
        {
          id: 1006,
          begin: 1,
          end: 2,
          week: 3,
          name: "党史",
          week_begin: 1,
          week_end: 8,
          place: "阶梯教室1",
          teacher: "李岩",
        },
        {
          id: 1007,
          begin: 5,
          end: 6,
          week: 3,
          name: "面向对象程序设计",
          week_begin: 1,
          week_end: 8,
          place: "南415",
          teacher: "寇艳艳",
        },
        {
          id: 1008,
          begin: 3,
          end: 4,
          week: 4,
          name: "数据可视化技术与应用",
          week_begin: 1,
          week_end: 16,
          place: "南215",
          teacher: "张娜",
        },
        {
          id: 1009,
          begin: 5,
          end: 6,
          week: 4,
          name: "WEB前端设计(js)",
          week_begin: 1,
          week_end: 16,
          place: "西405",
          teacher: "杨秋叶",
        },
        {
          id: 1010,
          begin: 9,
          end: 10,
          week: 4,
          name: "形势与政策",
          week_begin: 1,
          week_end: 4,
          place: "阶梯教室1",
          teacher: "王霄云",
        },
        {
          id: 1011,
          begin: 9,
          end: 10,
          week: 4,
          name: "形势与政策",
          week_begin: 1,
          week_end: 4,
          place: "阶梯教室1",
          teacher: "王霄云",
        },
        {
          id: 1012,
          begin: 1,
          end: 2,
          week: 5,
          name: "面向对象程序设计",
          week_begin: 1,
          week_end: 8,
          place: "南602",
          teacher: "寇艳艳",
        },
        {
          id: 1013,
          begin: 3,
          end: 4,
          week: 5,
          name: "数据采集与预处理",
          week_begin: 1,
          week_end: 16,
          place: "西306",
          teacher: "王磊",
        },
        {
          id: 1014,
          begin: 5,
          end: 6,
          week: 5,
          name: "WEB前端设计(js)",
          week_begin: 1,
          week_end: 16,
          place: "南215",
          teacher: "杨秋叶",
        },
      ],
    };
  },
  onLoad() {},
  methods: {
    getCourse(item) {
      console.log(item);
    },
  },
};


</script>



<style></style>
