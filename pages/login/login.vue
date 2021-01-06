<template>
	<form class="loginView" @submit="login">
		<view class="input-view">
			<view class="label-view"><text class="label">账号</text></view>
			<input class="input" type="text" placeholder="请输入用户名" name="nameValue" />
		</view>
		<view class="input-view">
			<view class="label-view"><text class="label">密码</text></view>
			<input class="input" type="password" placeholder="请输入密码" name="passwordValue" />
		</view>
		<view class="button-view">
			<button type="default" class="login" hover-class="hover" formType="submit">登录</button>
			<button type="default" class="register" hover-class="hover" @click="register">免费注册</button>
		</view>
	</form>
</template>

<script>
export default {
	data() {
		return {};
	},
	methods: {
		login(e) {
			console.log('得到账号:' + e.detail.value.nameValue + ';得到密码:' + e.detail.value.passwordValue);
		},
		register() {
			console.log('前往注册页面');
		}
	}
};
</script>

<style>
.loginView {
	display: flex;
	flex: 1;
	flex-direction: column;
	width: 750upx;
	min-height: 100vh;
	padding-top: 30upx;
}

.input-view {
	border-bottom-style: solid;
	border-bottom-width: 1upx;
	border-bottom-color: #ddd;
	background-color: #fff;
	flex-direction: row;
	width: 750upx;
	padding: 20upx 20upx;
	box-sizing: border-box;
}

.label-view {
	width: 100upx;
	height: 60upx;
	align-items: center;
	margin-right: 30upx;
}

.label {
	flex: 1;
	line-height: 60upx;
	font-size: 38upx;
	color: #555;
	text-align: left;
}

.input {
	flex: 1;
	height: 60upx;
	font-size: 38upx;
	align-items: center;
}

.button-view {
	width: 750upx;
	margin-top: 50upx;
	padding: 0 20upx;
	box-sizing: border-box;
	flex-direction: column;
}

button {
	width: 710upx;
	height: 80upx;
	line-height: 80upx;
	text-align: center;
	font-size: 38upx;
}

button.login {
	background-color: #ff80ab;
	color: #fff;
}

button.register {
	margin-top: 30upx;
	color: #ff80ab;
	background-color: #fff;
	border-color: #ff80ab;
	border-width: 2upx;
}

.register.hover,
.login.hover {
	opacity: 0.6;
}
</style>
