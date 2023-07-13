<template>
	<view class="container">
		<view class="my-info">
			<image src="@/static/avatar.jpg" class="avatar"></image>
			<view class="info-text">
				<text class="nickname">格谦辰</text>
				<text class="signature">个人签名</text>
			</view>
		</view>

		<view class="cell-group">
			<view class="cell">
				<image src="@/static/icon_password.png" class="icon-style"></image>
				<view class="section">
					<text>修改密码</text>
					<image src="@/static/icon_right.png" class="icon-right"></image>
				</view>
			</view>
			<navigator class="cell" url="/pages/help-center/help-center">
				<image src="@/static/icon_help.png" class="icon-style"></image>
				<view class="section">
					<text>帮助中心</text>
					<image src="@/static/icon_right.png" class="icon-right"></image>
				</view>
			</navigator>
			<view class="cell">
				<image src="@/static/icon_system.png" class="icon-style"></image>
				<view class="section">
					<text>系统版本</text>
					<image src="@/static/icon_right.png" class="icon-right"></image>
				</view>
			</view>
			<view class="cell">
				<image src="@/static/icon_logout.png" class="icon-style"></image>
				<view class="section">
					<text>退出登录</text>
					<image src="@/static/icon_right.png" class="icon-right"></image>
				</view>
			</view>

		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			};
		}
	}
</script>

<style lang="scss" scoped>
	.container {
		display: flex;
		flex-direction: column;
		height: var(100vh - 50);

		.my-info {
			display: flex;
			margin-top: 132rpx;
			padding: 0 40rpx;
			align-items: center;

			.avatar {
				width: 120rpx;
				height: 120rpx;
				border-radius: 100%;
				margin-right: 40rpx;
			}


			.info-text {
				display: flex;
				flex-direction: column;

				.nickname {
					font-weight: 700;
					font-size: 40rpx;
					color: #333;
				}

				.signature {
					font-size: 24rpx;
					color: #B6B6B6;
				}
			}

		}

		.cell-group {
			display: flex;
			flex-direction: column;
			margin-top: 92rpx;

			.cell {
				display: flex;
				justify-content: space-between;
				padding: 28rpx 24rpx 0;

				.section {
					display: flex;
					align-items: center;
					justify-content: space-between;
					flex: 1;
					border-bottom: 2rpx solid #F0F0F0;
					padding-bottom: 28rpx;
				}

				.icon-style {
					width: 48rpx;
					height: 48rpx;
					margin-right: 28rpx;
				}

				text {
					color: #333;
					font-size: 28rpx;
				}
			}


			.icon-right {
				width: 24rpx;
				height: 24rpx;
			}
		}
	}
</style>