<template>
	<view class="content">
		<view class="head">
			<uni-data-select class="head_select" v-model="selectNum" :localdata="range" @change="changeSelect">
			</uni-data-select>
			<view class="">好物分享</view>
			<u-search placeholder="输入搜索" v-model="keyword" shape="round" :clearabled="true" actionText="搜素"
				custom='searchList'></u-search>
			<u-button type="primary" text="设为首页"></u-button>
			<u-button type="primary" text="收藏本站"></u-button>
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
	.head {
		height: 70rpx;
		display: flex;
		background-color: antiquewhite;

		&_select {
			width: 132rpx;
			height: 100%;
		}
	}
</style>
