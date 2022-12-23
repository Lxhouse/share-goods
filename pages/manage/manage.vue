<template>
	<view class="content">
		<!-- <view class="head"> -->
		<u-subsection :list="list" :current="current" @change="changeSub"></u-subsection>
		<!-- </view> -->
		<view class="body">
			<pic-manage v-if="current===0" />

		</view>
		<view class="bottomBox">
			<view class="">类别：</view>
			<uni-data-select v-model="selectValue" :localdata="selectList" @change="changeSelect"></uni-data-select>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list: ['图片管理', '图片审核'],
				// 或者如下，也可以配置keyName参数修改对象键名
				// list: [{name: '未付款'}, {name: '待评价'}, {name: '已付款'}],
				current: 0,
				selectValue:0,
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
			changeSub(e) {
				this.current = e
			}
		}
	}
</script>

<style lang="scss">
	.content {
		background-color: #F8F8FF;
		height: 100%;
		padding-top: var(--status-bar-height);
		display: flex;
		flex-direction: column;
		padding-left: 20rpx;
		padding-right: 20rpx;
		position: absolute;
		top: 0;
		bottom: 0;
		left: 0;
		right: 0;

		.head {
			// margin: 0 10rpx;

		}

		.body {
			height: 100%;
			overflow-y: auto;
			overflow-x: hidden;
		}

		.bottomBox {
			display: flex;
			height: 100rpx;
			background-color: antiquewhite;
		}
	}
</style>
