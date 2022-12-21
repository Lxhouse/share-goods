<template>
	<view class="content">
		<view class="head">
			<uni-data-select class="head_select" :clear="false" v-model="selectNum" :localdata="range"
				@change="changeSelect">
			</uni-data-select>
			<view class="head_title">好物分享</view>
			<u-search placeholder="" v-model="keyword" shape="round" actionText="搜索" custom='searchList'></u-search>
			<u-button class="head_btn" type="primary" text="首页"></u-button>
			<u-button class="head_btn" type="primary" text="收藏" style="margin-left: 10rpx;"></u-button>
		</view>
		<view class="body">
			<Image-card :imgList="['/static/img/WechatIMG1815.jpeg']"></Image-card>
			<Image-card :imgList="['/static/img/WechatIMG1814.jpeg','/static/img/WechatIMG1813.jpeg']"></Image-card>
			<Image-card :imgList="['/static/img/WechatIMG1815.jpeg','/static/img/WechatIMG1814.jpeg']"></Image-card>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				selectNum: 0,
				keyword: '',
				range: [{
						value: 0,
						text: "按最新"
					},
					{
						value: 1,
						text: "按高赞"
					},
					{
						value: 2,
						text: "按收藏"
					},
				],
			}
		},
		onLoad() {

		},
		methods: {
			changeSelect(e) {
				console.log("e:", e);
			},
			searchList(_value) {

			}
		}
	}
</script>
<style lang="scss">
	.content {
		background-color: #F8F8FF;
		height: 100%;
		padding-top: var(--status-bar-height);
		padding-left: 20rpx;
		margin-right: 20rpx;
		display: flex;
		flex-direction: column;
		position: absolute;
		top: 0;
		bottom: 0;
		left: 0;
		right: 0;

		.head {
			height: 80rpx;
			display: grid;
			margin: 0 10rpx;
			align-items: center;
			grid-template-columns: 138rpx 128rpx auto 90rpx 90rpx;

			&_select {
				width: 138rpx;
				height: 100%;
			}

			&_title {
				display: flex;
				justify-content: center;
				align-items: center;
				font-size: 25rpx;
			}

			&_btn {
				width: 100%;
				height: 80%;
			}
		}

		.body {
			height: 100%;
			overflow: auto;
		}
	}
</style>
