<template>
	<view class="center">
		<view class="logo" @click="goLogin" :hover-class="!login ? 'logo-hover' : ''">
			<image class="logo-img" :src="login ? uerInfo.avatarUrl : avatarUrl"></image>
			<view class="logo-title">
				<text class="uer-name">Hi，{{ login ? uerInfo.name : '您未登录' }}</text>
				<text class="go-login navigat-arrow" v-if="!login">&#xe65e;</text>
			</view>
		</view>
		<view class="center-list">
			<view class="center-list-item border-bottom">
				<text class="list-icon">&#xe60c;</text>
				<text class="list-text">喜欢的活动</text>
				<text class="navigat-arrow">&#xe65e;</text>
			</view>
			<view class="center-list-item">
				<text class="list-icon">&#xe60d;</text>
				<text class="list-text">参加的活动</text>
				<text class="navigat-arrow">&#xe65e;</text>
			</view>
		</view>
		<view class="center-list">
			<view class="center-list-item border-bottom">
				<text class="list-icon">&#xe60b;</text>
				<text class="list-text">我的活动</text>
				<text class="navigat-arrow">&#xe65e;</text>
			</view>
			<view class="center-list-item">
				<text class="list-icon">&#xe61a;</text>
				<text class="list-text">创建活动</text>
				<text class="navigat-arrow">&#xe65e;</text>
			</view>
		</view>
		<view class="center-list">
			<view class="center-list-item border-bottom" @click="goAbout">
				<text class="list-icon">&#xe603;</text>
				<text class="list-text">关于</text>
				<text class="navigat-arrow">&#xe65e;</text>
			</view>
			<view class="center-list-item">
				<text class="list-icon">&#xe609;</text>
				<text class="list-text">帐号管理</text>
				<text class="navigat-arrow">&#xe65e;</text>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			login: false,
			avatarUrl: '../../static/logo.png',
			uerInfo: {}
		};
	},
	methods: {
		goLogin() {
			if (!this.login) {
				uni.navigateTo({
					url: '../login/login'
				});
			}
		},
		goAbout() {
			// #ifdef APP-PLUS
			uni.navigateTo({
				url: '/platforms/app-plus/about/about'
			});
			// #endif
			// #ifdef H5
			uni.navigateTo({
				url: '/platforms/h5/about/about'
			});
			// #endif
		}
	}
};
</script>

<style>
.center {
	flex-direction: column;
	min-height: 100vh;
}

.logo {
	width: 750upx;
	height: 240upx;
	padding: 20upx;
	box-sizing: border-box;
	background-color: #ff80ab;
	flex-direction: row;
	align-items: center;
}

.logo-hover {
	opacity: 0.8;
}

.logo-img {
	width: 150upx;
	height: 150upx;
	border-radius: 150upx;
}

.logo-title {
	height: 150upx;
	flex: 1;
	align-items: center;
	justify-content: space-between;
	flex-direction: row;
	margin-left: 20upx;
}

.uer-name {
	height: 60upx;
	line-height: 60upx;
	font-size: 38upx;
	color: #ffffff;
}

.go-login.navigat-arrow {
	font-size: 38upx;
	color: #ffffff;
}

.login-title {
	height: 150upx;
	align-items: self-start;
	justify-content: center;
	flex-direction: column;
	margin-left: 20upx;
}

.center-list {
	background-color: #ffffff;
	margin-top: 20upx;
	width: 750upx;
	flex-direction: column;
}

.center-list-item {
	height: 90upx;
	width: 750upx;
	box-sizing: border-box;
	flex-direction: row;
	padding: 0upx 20upx;
}

.border-bottom {
	border-bottom-width: 1upx;
	border-color: #c8c7cc;
	border-bottom-style: solid;
}

.list-icon {
	width: 40upx;
	height: 90upx;
	line-height: 90upx;
	font-size: 34upx;
	color: #ff80ab;
	text-align: center;
	font-family: texticons;
	margin-right: 20upx;
}

.list-text {
	height: 90upx;
	line-height: 90upx;
	font-size: 34upx;
	color: #555;
	flex: 1;
	text-align: left;
}

.navigat-arrow {
	height: 90upx;
	width: 40upx;
	line-height: 90upx;
	font-size: 34upx;
	color: #555;
	text-align: right;
	font-family: texticons;
}
</style>
