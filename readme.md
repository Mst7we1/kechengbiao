## 深柒课程表
简洁 美观 大方 优雅 支持自定义 轻松使用 支持显示或不显示非本周课程 支持动态切换周数
## 使用说明
1. 在插件市场下载并导入插件
2. 在需要使用课表的页面引入
3. 使用组件

## 特别提醒
为保证课表的显示效果，请在一个空白页中引入该组件，并在pages.json中对该页面的"style"属性添加 "navigationStyle": "custom"

## Props
| 参数名        | 类型   | 默认值                                                                                                         |描述            |  
|--------------|--------|----------------------------------------------------------------------------------------------------------------|---------------|
| image        | String | null                                                                                                           |背景图片，非必需 |
| time         | Array  | [['8:20', '9:00'], ['9:05', '9:45'], ['10:00', '10:40'], ..., ['20:25', '21:05']]                              |课程时间        |
| colorArrays  | Array  | ['#70eb55', '#ffc450', '#ff9bd7', '#86affe', '#58eea4', '#ffa17d', '#1cbbb4', '#6964ad', '#d42245', '#218285'] |课程卡片颜色    |
| timeColor    | String | #000000                                                                                                        |左侧时间颜色    |
| courseList   | Array  | []                                                                                                             |课程数组        |
| showNotWeek  | Boolean| true                                                                                                           |显示非本周课程  |
| week         | Number | 1                                                                                                              |当前教学周      |

## Events
| 事件名称      | 事件说明         | 返回值              |
|---------------|-----------------|--------------------|
| @click        | 点击课程卡片触发 | 对应课程的信息Object |

## courseList说明
courseList为保存课程的数组，结构如下：
~~~
[{
	id: 1000,//唯一即可
	begin: 2,//课程的开始节书数
	end: 4,//课程的结束节数
	week: 2,//星期几的课程
	name: '面向对象-JAVA实践教学',//课程名称
	week_begin: 8,//课程开始周
	week_end: 16,//课程结束周
	place: '理择楼314',//课程的教室地点
	teacher: '陆师'//任课教师
}//该课程在第8周到第16周的星期二的第二节到第四节
]
~~~

## 示例Demo
~~~
<template>
	<view>
		<SqTimetable @click="getCourse" :time="time" :image="image" :timeColor="timeColor" :courseList="courseList" :showNotWeek="true"
			:week="12"></SqTimetable>
	</view>
</template>
<script>
	import SqTimetable from '../../components/sq-timetable/sq-timetable.vue'
	export default {
		components: {
			SqTimetable
		},
		data() {
			return {
				time: [
					['8:20', '9:00'],
					['9:05', '9:45'],
					['10:00', '10:40'],
					['10:45', '11:25'],
					['11:30', '12:10'],
					['13:30', '14:10'],
					['14:15', '14:55'],
					['15:10', '15:50'],
					['15:55', '16:35'],
					['16:40', '17:20'],
					['18:00', '18:40'],
					['18:45', '19:25'],
					['19:40', '20:20'],
					['20:25', '21:05']
				],
				image: 'https://img04.sogoucdn.com/app/a/100520093/ca86e620b9e623ff-f4709b64c5c0ee80-852ef8b2f248787b2f289ae80f88038c.jpg',
				colorArrays: ['#70eb55', '#ffc450', '#ff9bd7', '#86affe', '#58eea4', '#ffa17d', '#1cbbb4', '#6964ad',
					'#d42245', '#218285'
				],
				timeColor: '#000000',
				courseList: [{
					id: 1000,
					begin: 2,
					end: 4,
					week: 2,
					name: '面向对象-JAVA实践教学',
					week_begin: 8,
					week_end: 8,//只在第8周有课
					place: '理泽楼314',
					teacher: '陆师'
				}, {
					id: 1001,
					begin: 1,
					end: 3,
					week: 4,
					name: '计算机网络（双语）',
					week_begin: 1,
					week_end: 16,//在第1-到第16周有课
					place: '理泽楼315',
					teacher: '刘师'
				}]
			}
		},
		onLoad() {

		},
		methods: {
			getCourse(item) {
				console.log(item)
			}
		}
	}
</script>
<style>
</style>
~~~

## 联系作者
xbos1314 / 979993911