<template>
	<view><uni-goods-nav :fill="true" :options="options" :buttonGroup="buttonGroup" @click="onClick" @buttonClick="buttonClick" class="goods-nav" /></view>
</template>

<script>
export default {
	data() {
		return {
			options: [
				{
					icon: 'headphones',
					text: '咨询'
				},
				{
					icon: 'hand-thumbsup',
					text: '赞',
					info: 4,
					infoBackgroundColor: '#ff0000'
				},
				{
					icon: 'hand-thumbsdown',
					text: '踩',
					infoBackgroundColor: 'gray',
					info: 2
				}
			],
			buttonGroup: [
				{
					text: '喜欢',
					backgroundColor: '#ff0000',
					color: '#fff'
				},
				{
					text: '参加',
					backgroundColor: '#FF80AB',
					color: '#fff'
				}
			]
		};
	},
	methods: {
		onClick(e) {
			uni.showToast({
				title: `点击${e.content.text}`,
				icon: 'none'
			});
		},
		buttonClick(e) {
			console.log(e);
			this.options[2].info++;
		}
	}
};
</script>

<style>
.goods-nav {
	display: flex;
	background-color: #ffffff;
	text-align: center;
	width: 100%;
	position: fixed;
	bottom: 1rpx;
	flex-direction: row;
}
</style>
