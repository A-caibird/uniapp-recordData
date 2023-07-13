<template>
	<view class="container">
		<image src="@/static/icon_logo.png" class="logo"></image>

		<u--form :model="modelValue">
			<view class="form">
				<text class="login-text">登录</text>
				<text class="login-tip">请使用账号密码登录</text>

				<view class="inputs">
					<u-form-item prop="modelValue.account">
						<u--input placeholder="用户账号" border="bottom" placeholderStyle="#C6C6C6" fontSize="28rpx"
							color="#333" :customStyle="inputStyle" v-model="modelValue.account"></u--input>
					</u-form-item>

					<u-form-item prop="modelValue.password">
						<u--input placeholder="密码" border="bottom" placeholderStyle="#C6C6C6" fontSize="28rpx"
							color="#333" :password="true" :customStyle="inputStyle" v-model="modelValue.password">
						</u--input>
					</u-form-item>

				</view>
			</view>

			<view class="login-btn">
				<u-button text="登录" color="#005AA8" :customStyle="loginBtnStyle" :disabled="disabled"
					@tap="login"></u-button>
			</view>
		</u--form>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				// 登录按钮是否禁用
				disabled: true,
				// 登录按钮自定义样式
				loginBtnStyle: {
					color: "#FFF"
				},
				// 输入框自定义样式
				inputStyle: {
					padding: "0 0 24rpx 0"
				},
				modelValue: {
					// 用户账号
					account: "",
					// 密码
					password: ""
				}
			};
		},
		watch: {
			modelValue: {
				deep: true,
				handler(newObj) {
					if (newObj.account !== "" && newObj.password !== "") {
						this.disabled = false
					} else {
						this.disabled = true
					}
				}
			}
		},
		methods: {
			login() {
				console.log("登录成功");
				uni.reLaunch({
					url: "/pages/index/index"
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.container {
		display: flex;
		flex-direction: column;
		height: 100vh;

		// logo样式
		.logo {
			width: 144rpx;
			height: 190rpx;
			margin-top: 220rpx;
			align-self: center;
		}

		.form {
			display: flex;
			flex-direction: column;
			margin-top: 88rpx;
			padding: 0 74rpx;

			.login-text {
				font-weight: 500;
				color: #333;
				font-size: 56rpx;
			}

			.login-tip {
				color: #999;
				font-size: 24rpx;
				margin-top: 8rpx;
			}


			.inputs {
				display: flex;
				flex-direction: column;
				gap: 56rpx;
				margin-top: 72rpx;
			}
		}

		// 登录按钮样式
		.login-btn {
			margin-top: 218rpx;
			box-sizing: border-box;
			padding: 0 48rpx;
		}

		::v-deep .u-button--disabled {
			opacity: 1 !important;
			background-color: #E2E2E2 !important;
			border-color: #E2E2E2 !important;
		}

		::v-deep .u-button__text span {
			font-size: 32rpx !important;
		}
	}
</style>