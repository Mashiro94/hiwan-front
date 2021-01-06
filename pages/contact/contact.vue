<template>
	<view>
		<uni-search-bar @confirm="search" @input="input" @cancel="cancel" />
		<uni-list :border="false">
			<uni-list-chat
				v-for="item in listData"
				:avatar-circle="true"
				:key="item.id"
				:title="item.author_name"
				:avatar="item.cover"
				:note="item.title"
				:time="item.published_at"
				:clickable="true"
				@click="goUser"
			></uni-list-chat>
		</uni-list>
	</view>
</template>

<script>
export default {
	data() {
		return {
			listData: [
				{
					id: 1,
					author_name: '小明',
					cover: '/static/uni.png',
					title: '上海吴彦祖',
					published_at: '男'
				},
				{
					id: 1,
					author_name: '小红',
					cover: '/static/latest/latest_3.jpg',
					title: '你好',
					published_at: '女'
				}
			]
		};
	},
	methods: {
		search(res) {
			uni.showToast({
				title: '搜索：' + res.value,
				icon: 'none'
			});
		},
		input(res) {
			this.searchVal = res.value;
		},
		cancel(res) {
			uni.showToast({
				title: '点击取消，输入值为：' + res.value,
				icon: 'none'
			});
		},
		goUser() {
			uni.navigateTo({
				url: '../user/user'
			});
		}
	}
};
</script>

<style></style>
