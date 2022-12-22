<template>
	<view class="card_body">
		<view class="card_body_card">
			<u-upload v-if="isUpload===true" v-for="itemImg in imgList"  name="6" accept="image" imageMode='scaleToFill' width="auto" multiple :maxCount="1">
				<image class="card_body_card__img" :src="itemImg" mode="scaleToFill" style="width: calc(100vw - 40rpx);"></image>
			</u-upload>
			<image v-else  v-for="itemImg in imgList" class="card_body_card__img" :src="itemImg" mode="scaleToFill"></image>
			<view v-if="showInlineBottom!==false" class="card_body_card__bottom">
				<image :src="actionList.isLike===0?iconList[0].no:iconList[0].yes" mode="aspectFill"
					style="width: 70rpx;height: 70rpx;" @click="changeStatus('like')"></image>
				<view class="card_body_card_num">{{actionList.likeNum}}</view>
				<image :src="actionList.isStep===0?iconList[1].no:iconList[1].yes" mode="aspectFit"
					style="width: 70rpx;height: 70rpx;" @click="changeStatus('step')"></image>
				<view class="card_body_card_num">{{actionList.stepNum}}</view>
				<image :src="actionList.isCollection===0?iconList[2].no:iconList[2].yes" mode="aspectFit"
					style="width: 70rpx;height: 70rpx;" @click="changeStatus('collection')"></image>
				<view class="card_body_card_num">{{actionList.collectionNum}}</view>
				<image :src="iconList[3].no" mode="aspectFit" style="width: 70rpx;height: 70rpx;"></image>
			</view>
		</view>
		<view v-if="showInlineBottom===false" class="card_body_card__down">
			<image :src="actionList.isLike===0?iconList[0].no:iconList[0].yes" mode="aspectFit"
				style="width: 70rpx;height: 70rpx;" @click="changeStatus('like')"></image>
			<view class="card_body_card_num">{{actionList.likeNum}}</view>
			<image :src="actionList.isStep===0?iconList[1].no:iconList[1].yes" mode="aspectFit"
				style="width: 70rpx;height: 70rpx;" @click="changeStatus('step')"></image>
			<view class="card_body_card_num">{{actionList.stepNum}}</view>
			<image :src="actionList.isCollection===0?iconList[2].no:iconList[2].yes" mode="aspectFit"
				style="width: 70rpx;height: 70rpx;" @click="changeStatus('collection')"></image>
			<view class="card_body_card_num">{{actionList.collectionNum}}</view>
			<!-- <image :src="iconList[3].no" mode="aspectFit" style="width: 70rpx;height: 70rpx;"></image> -->
		</view>
	</view>
</template>

<script>
	export default {
		name: "Image-card",
		props: ["imgList", "showInlineBottom", 'isUpload'],
		data() {
			return {
				actionList: {
					isLike: 1,
					likeNum: 123,
					isStep: 0,
					stepNum: 1234,
					isCollection: 0,
					collectionNum: 1234,

				},
				iconList: [{
					yes: '/static/icon/like.png',
					no: '/static/icon/unLike.png'
				}, {
					yes: '/static/icon/step.png',
					no: '/static/icon/unStep.png'
				}, {
					yes: '/static/icon/collection.png ',
					no: '/static/icon/unCollection.png '
				}, {
					no: '/static/icon/error.png'
				}]
			};
		},
		methods: {
			changeStatus(_name) {
				if (_name === 'like') {
					const temp = this.changeNum(this.actionList.isLike)
					this.actionList.isLike = temp
					temp === 1 ? this.actionList.likeNum++ : this.actionList.likeNum--
				} else if (_name === 'step') {
					const temp = this.changeNum(this.actionList.isStep)
					this.actionList.isStep = temp
					temp === 1 ? this.actionList.stepNum++ : this.actionList.stepNum--
				} else if (_name === 'collection') {
					const temp = this.changeNum(this.actionList.isCollection)
					this.actionList.isCollection = temp
					temp === 1 ? this.actionList.collectionNum++ : this.actionList.collectionNum--
				}
			},
			changeNum(_num) {
				return _num === 1 ? 0 : 1
			}
		},

	}
</script>

<style lang="scss">
	.card_body {
		width: 100%;
		// margin-top: 20rpx;
	

		&_card {
			position: relative;

			// height: fit-content;

			&__img {
				height: 500rpx;
				width: 100%;
				margin-bottom: -10rpx;
			}

			&_num {
				font-size: 40rpx;
				font-weight: 900;
			}

			&__bottom {
				height: 120rpx;
				width: 100%;
				position: absolute;
				bottom: 0;
				left: 0;
				display: grid;
				grid-template-columns: repeat(3, 80rpx 100rpx) auto;
				align-items: center;
				justify-self: center;
				margin: 0 15rpx;
				align-self: center;
			}

			&__down {
				height: 100rpx;
				width: 100%;
				display: grid;
				grid-template-columns: repeat(3, 80rpx 100rpx) auto;
				align-items: center;
				justify-self: center;
				margin: 0 15rpx;
				align-self: center;
			}
		}
	}
</style>
