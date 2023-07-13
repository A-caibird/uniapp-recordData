<template>
	<view class="container">
		<view class="layout-fixed">
			<view class="search">
				<u-search :clearabled="false" :searchIconSize="32" shape="square" v-model="keyword" bgColor="#F5F6FA"
					placeholder="搜索采样记录" :showAction="false" height="72rpx" :inputStyle="inputStyle"
					placeholderColor="#ACACAC" color="#333"></u-search>
				<view class="filter">
					<image src="@/static/icon_time.png" class="time-icon"></image>
					<text class="time-text">时间筛选</text>
				</view>
			</view>
		</view>
		<view class="list">
			<view class="u-page">
				<u-list>
					<u-list-item v-for="(item, index) in 31" :key="index">
						<view class="item" @tap="listDetail">
							<text class="serial-number">{{index + 1 > 9 ? index + 1 : `0${index + 1}`}}</text>
							<u-cell>
								<view slot="title">
									<view>
										<image src="@/static/icon_record.png" class="icon-record"></image>
										<text class="u-cell-text">高新区绿城浙砾XCL02-03-07a地块房产项目三标段</text>
									</view>

									<view class="record-status">
										<template v-if="isRecord">
											<text class="time-date">2023.07.07</text>
											|
											<text class="continue-record">继续录入</text>
										</template>
										<template v-else>
											<text class="wait-record">待录入</text>
										</template>
									</view>
								</view>
							</u-cell>
						</view>
					</u-list-item>
				</u-list>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				// 搜索的内容
				keyword: "",
				// 输入框样式
				inputStyle: {
					fontSize: "28rpx",
					padding: "16rpx",
					paddingLeft: "0",
					boxSizing: "border-box"
				},
				isRecord: false
			};
		},
		methods: {
			listDetail() {
				uni.navigateTo({
					url: "/pages/building-list/building-list"
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.container {
		position: relative;
		display: flex;
		flex-direction: column;
		height: 100vh;
		padding: 0 24rpx;
		gap: 60rpx;

		.layout-fixed {
			height: 72rpx;
			margin-top: 88rpx;

			// 搜索框样式
			.search {
				position: fixed;
				top: 88rpx;
				left: 0;
				display: flex;
				align-items: center;
				z-index: 999;
				justify-content: space-between;
				background-color: #FFF;
				padding: 0 24rpx;
				width: 100vw;
				box-sizing: border-box;


				.filter {
					display: flex;
					margin-left: 16rpx;

					// 时间筛选图标样式
					.time-icon {
						width: 32rpx;
						height: 32rpx;
						margin-right: 4rpx;
					}

					// 时间筛选文字样式
					.time-text {
						color: #005AA8;
						font-size: 24rpx;
					}
				}
			}
		}

		// 列表样式
		.list {
			position: absolute;
			top: 160rpx;
			left: 0;
			bottom: 0rpx;
			overflow: hidden;
			margin-top: 68rpx;

			// 列表项样式
			.item {
				display: flex;
				margin-bottom: 36rpx;
				padding: 0 24rpx;


				// 列表序号样式
				.serial-number {
					font-size: 36rpx;
					color: #D9D9D9;
					margin-right: 26rpx;
				}

				// 列表单元格样式
				.u-cell {
					flex-shrink: 1;

					// 列表文字样式
					.u-cell-text {
						font-size: 30rpx;
						height: 84rpx;
						flex: 1;
						line-height: 42rpx;
					}

					// 列表图标样式
					.icon-record {
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
							margin-left: 10rpx;
							color: #005AA8;
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
			height: 172rpx;
			display: block;
		}
	}
</style>