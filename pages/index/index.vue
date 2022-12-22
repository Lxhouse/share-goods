<template>
	<view class="content">
		<view class="head">
			<uni-data-select class="head_select" :clear="false" v-model="selectNum" :localdata="range"
				@change="changeSelect">
			</uni-data-select>
			<view class="head_title">好物分享</view>
			<u-search placeholder="" v-model="keyword" shape="round" actionText="搜索" custom='searchList'></u-search>
			<u-button class="head_btn" type="primary" @click="setHome(this)" text="首页"></u-button>
			<u-button class="head_btn" type="primary" @click="shoucang" text="收藏" style="margin-left: 10rpx;">
			</u-button>
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
		mounted() {
			console.log(window)
		},
		methods: {
			changeSelect(e) {
				console.log("e:", e);
			},
			searchList(_value) {

			},
			setHome(obj) {
				let vrl = window.location
				console.log(123321, {
					vrl
				}, document.title)
				try {
					obj.style.behavior = 'url(#default#homepage)';
					obj.setHomePage(vrl);
				} catch (e) {
					if (window.netscape) {
						try {
							netscape.security.PrivilegeManager.enablePrivilege("UniversalXPConnect");
						} catch (e) {
							alert(
								"此操作被浏览器拒绝！\n请在浏览器地址栏输入“about:config”并回车\n然后将 [signed.applets.codebase_principal_support]的值设置为'true',双击即可。");
						}
						var prefs = Components.classes['@mozilla.org/preferences-service;1'].getService(Components
							.interfaces.nsIPrefBranch);
						prefs.setCharPref('browser.startup.homepage', vrl);
					} else {
						alert("您的浏览器不支持，请按照下面步骤操作：1.打开浏览器设置。2.点击设置网页。3.输入：" + vrl + "点击确定。");
					}
				}
			},
			shoucang() {
				const sTitle = document.title;
				const sURL = window.location;
		
		            // sURL = encodeURI(sURL); 
		        try{   
		  
		            window.external.addFavorite(sURL, sTitle);   
		  
		        }catch(e) {   
		  
		            try{   
		  
		                window.sidebar.addPanel(sTitle, sURL, "");   
		  
		            }catch (e) {   
		  
		                alert("加入收藏失败，请使用Ctrl+D进行添加,或手动在浏览器里进行设置.");
		  
		            }   
		  
		        }
		  
		    
			}
		}
	}
</script>
<style lang="scss">
	.content {
		background-color: #F8F8FF;
		height: 100%;
		padding-top: var(--status-bar-height);
		width: calc(100% - 40rpx);
		padding-left: 20rpx;
		padding-right: 20rpx;
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
			overflow-y: auto;
			overflow-x: hidden;
		}
	}
</style>
