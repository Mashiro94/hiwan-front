<template>
	<view class="index">
		<uni-card
			v-for="(item, index) in list"
			:key="index"
			:isShadow="true"
			:title="item.name"
			:subTitle="item.date"
			thumbnail="/static/latest/latest_3.jpg"
			mode="title"
			:extra="item.beginTime"
			note="true"
			@click="goDetail"
		>
			<view>
				<view class="image-box"><image class="image" mode="aspectFill" :src="item.src" /></view>
				<view class="content-box">
					<text class="content-box-text">{{ item.location }}</text>
				</view>
			</view>
			<template slot="footer">
				<view class="footer-box">
					<view @click.stop="footerClick('喜欢')"><text class="footer-box__item">喜欢</text></view>
					<view @click.stop="footerClick('参加')"><text class="footer-box__item">参加</text></view>
					<view @click.stop="footerClick('屏蔽')"><text class="footer-box__item">屏蔽</text></view>
				</view>
			</template>
		</uni-card>
	</view>
</template>

<script>
export default {
	data() {
		return {
			list: []
		};
	},
	onLoad() {
		this.getData();
	},
	onPullDownRefresh() {
		this.getData();
	},
	methods: {
		getData() {
			this.list = [
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
			];
		},
		goDetail() {
			uni.navigateTo({
				url: '../detail/detail'
			});
		}
	}
};
</script>

<style>
.image-box {
	/* #ifndef APP-NVUE */
	display: flex;
	flex-direction: column;
	/* #endif */
	height: 350rpx;
	overflow: hidden;
}

.image {
	/* #ifndef APP-NVUE */
	width: 100%;
	height: 100%;
	/* #endif */
	flex: 1;
}

.content-box {
	padding-top: 20rpx;
}

.content-box-text {
	font-size: 12px;
	line-height: 22px;
}

.footer-box {
	/* #ifndef APP-NVUE */
	display: flex;
	/* #endif */
	justify-content: space-between;
	flex-direction: row;
}

.footer-box__item {
	align-items: center;
	padding: 2px 0;
	font-size: 12px;
	color: #666;
}
</style>
