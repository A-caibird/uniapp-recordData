<template>
	<view class="container">
		<view class="layout-fixed">
			<text class="title">数据采集</text>
		</view>

		<view class="list">
			<view class="u-page">
				<u-list>
					<u-list-item v-for="(item, index) in 3" :key="index">
						<view class="item">
							<text class="serial-number">{{index + 1 > 9 ? index + 1 : `0${index + 1}`}}</text>
							<u-cell>
								<view slot="title">
									<view>
										<image src="@/static/icon_building.png" class="icon-building"></image>
										<text class="u-cell-text">17幢</text>
									</view>

									<view class="record-status">
										<text class="time-date">2023.07.07</text>
										|
										<image src="@/static/icon_continue.png" class="icon-continue"></image>
										<text class="continue-record" @click="contineRecord">继续录入</text>
									</view>
								</view>
							</u-cell>
						</view>
					</u-list-item>
				</u-list>
			</view>
		</view>

		<image src="@/static/icon_add.png" class="icon-add"></image>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			};
		},
		methods: {
			contineRecord() {
				uni.navigateTo({
					url: "/pages/colletDetail/colletDetail"
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
		padding: 0 24rpx;

		.icon-add {
			position: fixed;
			bottom: 108rpx;
			right: 72rpx;
			width: 104rpx;
			height: 104rpx;
		}

		.layout-fixed {
			height: 41.6rpx;
			margin-top: 88rpx;
			margin-bottom: 88rpx;
			background-color: #FFF;

			.title {
				position: fixed;
				top: 88rpx;
				z-index: 999;
				display: flex;
				align-items: center;
				font-weight: 500;
				color: #333;
				font-size: 32rpx;

				background-color: #FFF;
				width: 100vw;
				padding-bottom: 44rpx;

				&::before {
					content: '';
					display: block;
					width: 6rpx;
					height: 30rpx;
					border-radius: 2rpx;
					background-color: #005AA8;
					margin-right: 8rpx;
				}
			}
		}

		// 列表样式
		.list {
			flex: 1;
			overflow: hidden;

			// 列表项样式
			.item {
				display: flex;
				margin-bottom: 36rpx;


				// 列表序号样式
				.serial-number {
					font-size: 36rpx;
					color: #D9D9D9;
					margin-right: 26rpx;
				}

				// 列表单元格样式
				.u-cell {
					flex: 1;

					// 列表文字样式
					.u-cell-text {
						font-size: 30rpx;
						height: 42rpx;
						flex: 1;
						line-height: 42rpx;
						color: #333;
					}

					// 列表图标样式
					.icon-building {
						width: 32rpx;
						height: 32rpx;
						vertical-align: middle;
						margin-right: 15rpx;
					}

					// 录入状态样式
					.record-status {
						display: flex;
						margin-top: 16rpx;
						font-size: 26rpx;
						color: #ACACAC;

						.time-date {
							margin-right: 10rpx;
						}

						.continue-record {
							color: #005AA8;
						}

						.icon-continue {
							width: 32rpx;
							height: 32rpx;
							vertical-align: middle;
							margin: 0 14rpx;
						}

						// 待录入样式
						.wait-record {
							color: #FD922F;
							font-size: 26rpx;
						}
					}
				}
			}
		}

		::v-deep .u-cell__body {
			padding: 0 0 36rpx 0;
			display: block;
			box-sizing: border-box;
		}
	}
</style>