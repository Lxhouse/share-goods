<template>
	<view style="width: 100%;">
		<view class="body">
		<manage-item></manage-item>
		<manage-item></manage-item>
		</view>
	</view>
</template>

<script>
	export default {
		name: "pic-manage",
		data() {
			return {
			
			};
		},
		methods: {
			maskClick(e) {
				console.log('maskClick事件:', e);
			}
		}
	}
</script>

<style lang="scss">
	.body {
		height: 100%;
		overflow: auto;
		&_opt{
			height: 100rpx;
			display: grid;
			// grid-template-columns: 700rpx auto;
		}
	}
</style>
