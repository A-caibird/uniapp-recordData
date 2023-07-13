<template>
	<view class="content">
		<view class="j1" :class="{'ziti1':isziti1,'ziti2':isziti2}" @click="click1">
			基本信息
		</view>
		<view class="j2" :class="{'ziti1':isziti2,'ziti2':isziti1}" @click="click2">
			采集数据
		</view>

		<view :class="{'xia1':isziti1,'xia2':isziti2}">
		</view>

		<view v-if="isziti1" class="mo1">
			<view class='name'>
				工程名称
			</view>
			<view>
				<u--input placeholder="高新区绿城浙烁XCL02-03-07a地块房产项目三标段" class="input1" border="none"
					v-model.trim:value="form.name"></u--input>
			</view>
			<view class="diliv" style="position:absolute;top:340rpx;left:24rpx">
			</view>
			<view class='hetong'>
				工程合同
			</view>
			<view>
				<u--input placeholder="22K03" class="input2" border="none" v-model.trim:value="form.hetong"></u--input>
			</view>
			<view class="diliv" style="position:absolute;top:492rpx;left:24rpx;">
			</view>
			<view class='lou'>
				楼 (幢) 号
			</view>
			<view class="bao">
				<u--input placeholder="17" class="input3" border="none" v-model.trim:value="form.lou"></u--input>
			</view>
			<view class='jcyj'>
				检测依据
			</view>
			<view>
				<u--input placeholder="GB  50325-2020" class="input4" border="none"
					v-model.trim:value="form.jcyj"></u--input>
			</view>
			<view class="diliv" style="position:absolute;top:810rpx;left:24rpx">
			</view>
			<view class="fzsb">
				辅助设备
			</view>
			<view>
				<view class="zu1">
					<text class="lzu1">
						KQ-
					</text>
					<text class="zzu1">
						<u--input placeholder="请输入" class="z1input" border="none" v-model.trim:value="form.f1">
						</u--input>
					</text>
					<text class="rzu1">
						/AS837 温湿度计
					</text>
				</view>
				<view class="zu2">
					<text class="lzu2">
						KQ-
					</text>
					<text class="zzu2">
						<u--input placeholder="请输入" class="z2input" border="none" v-model.trim:value="form.f2">
						</u--input>
					</text>
					<text class="rzu2">
						/DYM3空盒气压表
					</text>
				</view>
				<u-button text="下一步" class="but"></u-button>
			</view>
		</view>

		<view v-if="isziti2" class="mo2">
			<view class="Input" @click="to(1)">{{rec.n1}}</view>
			<view class="Input" @click="to(2)">{{rec.n2}}</view>
			<view class="Input" @click="to(3)">{{rec.n3}}</view>
			<view class="Input" @click="to(4)">{{rec.n4}}</view>
			<view class="divi">
			</view>
			<view class="Input input2" @click="tow(1)">{{rec.w1}}</view>
			<view class="Input input3" @click="tow(2)">{{rec.w2}}</view>
			<view class="butgrp">
				<u-button text="离线保存" class="bt1">
				</u-button>
				<u-button text="确定提交" class="bt2" @click="sub"></u-button>
			</view>
			<view class="smt" v-if="smt">
				<view class="subfont">
					提交成功
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				isziti1: true,
				isziti2: false,
				form: {
					name: '',
					hetong: '',
					lou: '',
					jcyj: '',
					f1: '',
					f2: '',
				},
				rec: {
					n1: '室内数据组①  (未填写)',
					n2: '室内数据组②  (未填写)',
					n3: '室内数据组③  (未填写)',
					n4: '室内数据组④  (未填写)',
					w1: '室外数据组①  (未填写)',
					w2: '室外数据组②  (未填写)',
				},
				smt: false,
				issave: true
			}
		},
		onLoad() {
			uni.$on('issave', issave => {
				this.issave = issave;
			})
		},
		onUnload() {
			uni.$off("issave");
		},
		methods: {
			click1() {
				this.isziti1 = true;
				this.isziti2 = false;
			},
			click2() {
				this.isziti2 = true;
				this.isziti1 = false;
			},
			sub() {
				this.submit();
			},
			submit() {
				this.smt = true;
				setTimeout(() => {
					this.smt = false;
				}, 1000);
			},
			to(num) {
				num-=1;
				let a = '../in_doors/in_doors?id=' + num;
				uni.navigateTo({
					url: a
				})
			},
			tow(num) {
				num-=1;
				let a = "../out_doors/out_doors?id=" + num;
				uni.navigateTo({
					url: a
				})
			}
		}
	}
</script>

<style lang="less" scoped>
	@import url('./style.less');
</style>