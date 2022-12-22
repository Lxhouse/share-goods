<template>
	<view class="content">
		<!-- <view class="head"> -->
			<u-subsection :list="list" :current="current" @change="changeSub"></u-subsection>
		<!-- </view> -->
		<view class="body">
			<pic-manage v-if="current===0" />
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
				current: 0
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
		margin-right: 20rpx;
		position: absolute;
		top: 0;
		bottom: 0;
		left: 0;
		right: 0;

		.head {
			// margin: 0 10rpx;

		}
		.body {
			width: 100%;
			height: 100%;
			overflow: auto;
		}
	}
</style>
