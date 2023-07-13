<template>
	<view class="container">
		<view class="cell-group">
			<view class="cell">
				<view class="section">
					<text>用户手册</text>
					<image src="@/static/icon_right.png" class="icon-right"></image>
				</view>
			</view>
			<view class="cell">
				<view class="section">
					<text>数据录入不能离线保存吗？</text>
					<image src="@/static/icon_right.png" class="icon-right"></image>
				</view>
			</view>
			<view class="cell">
				<view class="section">
					<text>修改密码怎么操作</text>
					<image src="@/static/icon_right.png" class="icon-right"></image>
				</view>
			</view>
			<view class="cell">
				<view class="section">
					<text>个人信息怎么修改不了</text>
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
		height: var(100vh - 44);

		.cell-group {
			display: flex;
			flex-direction: column;
			margin-top: 40rpx;

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