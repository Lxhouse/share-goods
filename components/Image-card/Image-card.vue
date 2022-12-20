<template>
	<view class="card_body">
		<view class="card_body_card">
			<image class="card_body_card__img" src="@/static/img/WechatIMG1815.jpeg" mode="aspectFill"></image>
			<view class="card_body_card__bottom">
				<image src="@/static/icon/unLike.png" mode="aspectFit" style="width: 80rpx;height: 80rpx;"></image>
				<image src="@/static/icon/unStep.png" mode="aspectFit" style="width: 80rpx;height: 80rpx;"></image>
				<image src="@/static/icon/unCollection.png" mode="aspectFit" style="width: 80rpx;height: 80rpx;">
				</image>
				</image>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: "Image-card",
		data() {
			return {

			};
		}
	}
</script>

<style lang="scss">
	.card_body {
		margin-top: 20rpx;

		&_card {
			position: relative;
			height: 500rpx;

			background-color: antiquewhite;

			&__img {
				height: 100%;
				width: 100%;
			}

			&__bottom {
				height: 20%;
				width: 100%;
				position: absolute;
				bottom: 0;
				left: 0;
				display: grid;
				grid-template-columns: 100rpx 100rpx 100rpx 100rpx auto;
				align-items: center;
			}
		}
	}
</style>
