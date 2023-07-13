<template>
	<view class="view">

		<view class="n1name">
			<view class="f">
				室外数据组
			</view>
			<view class="m">
				{{serialNumber[index]}}
			</view>
			<view class="b" v-if="disp">
				（未填写）
			</view>
		</view>

		<view class="item1" v-if="false">
			<view class="Gfont f1">
				测点房间名称或轴线
			</view>
			<view class="i1iv">
				<u--input class="input1" border="none" placeholder="请输入" v-model="form[0]">
				</u--input>
			</view>
		</view>

		<!-- <view class="divi d1"></view> -->

		<view class="item2">

			<view class="Gfont f2">
				室外样布点示意图（到楼距离m）
			</view>

			<view class="shiyi">
				<view>
					<image src="../../static/measurement.png" class="img">
					</image>
				</view>
			</view>

		</view>

		<view class="item3">
			<view class="i3">
				<view class="f">
					①
				</view>
				<view class="m">
					段距离
				</view>
			</view>

			<view class="i3v">
				<u--input placeholder="请输入" class="input1" border="none" v-model="form[1]"></u--input>
			</view>
		</view>

		<view class="item4">
			<view class="i4">
				<view class="f">
					②
				</view>
				<view class="m">
					段距离
				</view>
			</view>
			<view class="i4v">
				<u--input placeholder="请输入" class="input1" border="none" v-model="form[2]"></u--input>
			</view>
		</view>

		<view class="divi d2"></view>
		<view class="move">
			<view class="item5">
				<view class="Gfont f3">
					测点编号
				</view>
				<view class="iv">
					<u--input class="input1" border="none" placeholder="请输入" v-model="form[3]"></u--input>
				</view>
			</view>

			<view class="divi d3"></view>

			<view class="item6">
				<view class="Gfont f4">
					采样器组号
				</view>
				<view class="iv">
					<u--input border="none" class="input1" placeholder="请输入" v-model="form[4]">
					</u--input>
				</view>
			</view>

			<view class="divi d4"></view>

			<view class="item7">
				<view class="Gfont f4">
					采样点环境
				</view>
				<view class="item7-1">
					<view class="Gfont2 f1">
						温度（­°C）
					</view>
					<view class="iv">
						<u--input placeholder="请输入" border="none" class="input1" v-model="form[5]">
						</u--input>
					</view>
				</view>
				<view class="item7-2">
					<view class="Gfont2 f2">
						湿度（­%）
					</view>
					<view class="iv">
						<u--input placeholder="请输入" border="none" class="input1" v-model="form[6]">
						</u--input>
					</view>
				</view>
				<view class="item7-3">
					<view class="Gfont2 f3">
						大气压（­KPa）
					</view>
					<view class="iv">
						<u--input placeholder="请输入" border="none" class="input1" v-model="form[7]">
						</u--input>
					</view>
				</view>
				<view class="divi1"></view>
			</view>

			<view class="item8" v-if="true">
				<view class="Gfont f5">
					房间门窗关闭起止时间
				</view>
				<view class="item8-1">
					<view class="iv1">
						<u--input class="input1" style="width: 256rpx;
			height: 40rpx;" placeholder="请选择起始时间" border="none" v-model="form[8]"></u--input>

					</view>

					<view class="m">
						-
					</view>

					<view class="iv3">
						<u--input placeholder='请选择结束时间' class="input1" style="width: 256rpx;
			height: 40rpx;left:400rpx" v-model="form[9]" border="none">
						</u--input>
					</view>
				</view>
			</view>

			<view class="divi d5">

			</view>

			<view class="item9" v-if="true">
				<view class="title">
					采样体积V1（L）：J为20，B、T均为10
				</view>
				<view class="item9-1">
					<view class="title">
						采样起止时间
					</view>
					<view class="input">
						<view class="iv1">
							<u--input class="input1" style="width: 256rpx;
								height: 40rpx;" placeholder="请选择起始时间" border="none" v-model="form[10]"></u--input>

						</view>

						<view class="m">
							-
						</view>

						<view class="iv3">
							<u--input placeholder='请选择结束时间' class="input1" style="width: 256rpx;
								height: 40rpx;left:400rpx" border="none" v-model="form[11]"></u--input>
						</view>
					</view>

				</view>
				<view class="item9-2">
					<view class="title">
						甲醛（J）
					</view>
					<view class="iv">
						<u--input class="input1" placeholder="请输入" border="none" v-model="form[12]">
						</u--input>
					</view>
				</view>
				<view class="item9-3">
					<view class="title">
						苯系物（B）、TVOC（T）
					</view>
					<view class="iv">
						<u--input class="input1" placeholder="请输入" border="none" v-model="form[13]">
						</u--input>
					</view>
				</view>
				<view class="item9-4">
					<view class="title">
						氨（A）
					</view>
					<view class="iv">
						<u--input class="input1" placeholder="请输入" border="none" v-model="form[14]">
						</u--input>
					</view>
				</view>
			</view>
		</view>

		<view class="bdiv" v-if="true">
			<u-button class="button" @click="save">
				<view class="txt">
					确定保存
				</view>
			</u-button>>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				form: ['', '', '', '', '', '', '', '', '', '', '', '', '', '', ''],
				issave: false,
				serialNumber: ['①', '②', '③', '④'],
				index:1
			};
		},
		methods: {
			back() {
				uni.navigateBack({
					delta: 1
				})
			},
			check() {
				for (let i = 1; i <= 15; i++) {
					if (!this.form[i])
						return false;
				}
				return true;
			},
			save() {
				// this.issave = this.check();
				this.issave=false;
				if (this.issave)
					uni.$emit('issave', false)
			}
		},
		created() {

		},
		computed: {
			disp: function() {
				for (let i = 0; i < 16; i++) {
					if (this.form[i]) {
						return false;
					}
				}
				return true;
			},

		},
		onLoad: function(option) { //option为object类型，会序列化上个页面传递的参数
		  this.index=option.id;
		}
	}
</script>


<style lang="less" scoped>
	@import url("./style.less");
</style>