<template>
	<view>
		<Image-card :imgList="['/static/img/WechatIMG1815.jpeg']" :showInlineBottom="false" :isUpload="true"></Image-card>
		<view class="body_opt">
			<uni-datetime-picker v-model="range" type="daterange" @maskClick="maskClick" />
		</view>
		<view class="body_opt2">
			<view class="">类别：</view>
			<uni-data-select v-model="selectValue" :localdata="selectList" @change="change"></uni-data-select>
			<view class="">显示：</view>
			<u-switch v-model="show" @change="changeShow"></u-switch>
			<u-button type="primary" text="改图"></u-button>
			<u-button type="error" style='margin-left: 20rpx;' text="删除"></u-button>
		</view>
		<view class="body_opt3">
			<u--input v-model="info.keyWord" placeholder="商品名称/关键字" border="surround" clearable></u--input>
			<u--input v-model="info.address" placeholder="商品地址" border="surround" clearable></u--input>
		</view>
	</view>
</template>

<script>
	export default {
		name: "manage-item",
		data() {
			return {
				range: ['2021-02-1', '2021-3-28'],
				selectValue: 1,
				show: true,
				info: {
					keyWord: '',
					address: ''
				},
				selectList: [{
						value: 0,
						text: "活动商品"
					},
					{
						value: 1,
						text: "性价比"
					},
					{
						value: 2,
						text: "超低价"
					}, {
						value: 3,
						text: "高性能"
					},
				],
			};
		},
		methods: {
			changeShow(e) {
				console.log(e)
				this.show = e
			}
		}
	}
</script>

<style lang="scss">
	.body_opt {
		height: 100rpx;
		display: grid;
		// grid-template-columns: 700rpx auto;
	}

	.body_opt2 {
		height: 60rpx;
		display: grid;
		grid-template-columns: repeat(1, 100rpx 200rpx) 100rpx 120rpx 80rpx 80rpx;
		align-items: center;
		justify-self: center;
	}

	.body_opt3 {
		margin-top: 30rpx;
	}
</style>
