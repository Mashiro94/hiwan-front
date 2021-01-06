<template>
	<view>
		<view class="uni-title uni-common-pl">活动城市</view>
		<view class="uni-list">
			<view class="uni-list-cell">
				<view class="uni-list-cell-left">当前选择</view>
				<view class="uni-list-cell-db">
					<picker @change="bindPickerChange" :value="index" :range="array">
						<view class="uni-input">{{ array[index] }}</view>
					</picker>
				</view>
			</view>
		</view>

		<view class="uni-title uni-common-pl">活动日期</view>
		<view class="uni-list">
			<view class="uni-list-cell">
				<view class="uni-list-cell-left">当前选择</view>
				<view class="uni-list-cell-db">
					<picker mode="date" :value="date" :start="startDate" :end="endDate" @change="bindDateChange">
						<view class="uni-input">{{ date }}</view>
					</picker>
				</view>
			</view>
		</view>

		<view>
			<uni-card v-for="(item, index) in resultList" :key="index" :title="item.name" :extra="item.beginTime" isShadow>
				<text class="content-box-text">{{ item.location }}</text>
			</uni-card>
		</view>
	</view>
</template>
<script>
export default {
	data() {
		const currentDate = this.getDate({
			format: true
		});
		return {
			title: 'picker',
			array: ['上海', '北京', '广州', '深圳'],
			index: 0,
			date: currentDate,
			resultList: [
				{
					name: '单身︱德州扑克(德扑)桌游畅玩专场！欢乐交友~',
					date: '2021.1.14',
					beginTime: '15:00',
					location: '（上海长宁）上岛咖啡(中山公园店)︱汇川路99号新时空国际商务广场2楼(地铁中山公园7口)',
					src: 'http://wimg.huodongxing.com/logo/202009/5562523177200/103982362542843_v2.jpg'
				},
				{
					name: '单身︱狼人杀桌游专场！找到你的盖世预言家~',
					date: '2020.1.13',
					beginTime: '15:00',
					location: '（上海长宁）上岛咖啡(中山公园店)︱汇川路99号新时空国际商务广场2楼(地铁中山公园7口)',
					src: 'http://wimg.huodongxing.com/logo/202009/8562433930100/563982364023396_v2.jpg'
				}
			]
		};
	},
	computed: {
		startDate() {
			return this.getDate('start');
		},
		endDate() {
			return this.getDate('end');
		}
	},
	methods: {
		bindPickerChange: function(e) {
			console.log('picker发送选择改变，携带值为', e.target.value);
			this.index = e.target.value;
		},
		bindDateChange: function(e) {
			this.date = e.target.value;
		},
		getDate(type) {
			const date = new Date();
			let year = date.getFullYear();
			let month = date.getMonth() + 1;
			let day = date.getDate();

			if (type === 'start') {
				year = year - 60;
			} else if (type === 'end') {
				year = year + 2;
			}
			month = month > 9 ? month : '0' + month;
			day = day > 9 ? day : '0' + day;
			return `${year}-${month}-${day}`;
		}
	}
};
</script>
<style></style>
