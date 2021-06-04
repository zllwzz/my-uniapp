<template>
	<view class="navbar">
		<view class="navbar-fixed">
			<!-- #ifndef H5 -->
			<view :style="{height:statusBarHeight+'px'}"></view>
			<!-- #endif -->
			
			<view class="navbar-content" :style="{height:menuHeigt+'px',width: navbarWidth+'px'}">
				<view class="navbar-search">
					<view class="navbar-search_icon">
						<!-- <text class="iconfont icon-search"></text> -->
						<uni-icons type="search" size="16" color="#999"></uni-icons>
					</view>
					<view class="navbar-search_text">
						uni-app/vue
					</view>
				</view>
			</view>
		</view>
		<view :style="{height: menuHeigt+statusBarHeight+'px'}"></view>
	</view>
</template>

<script>
	export default {
		name:"navbar",
		data() {
			return {
				statusBarHeight: 0,
				menuHeigt: 45,
				navbarWidth: '100%',
			};
		},
		created() {
			const info = uni.getSystemInfoSync()
			this.statusBarHeight = info.statusBarHeight
			
			// 获取胶囊的位置
			// #ifndef APP-PLUS || H5 || MP-ALIPAY
			const menuButtonInfo = uni.getMenuButtonBoundingClientRect();
			// console.log(menuButtonInfo)
			// 导航栏的高度 = (胶囊底部高度 - 状态栏的高度) + （胶囊顶部高度 - 状态栏的高度）
			this.menuHeigt = (menuButtonInfo.bottom - this.statusBarHeight) + (menuButtonInfo.top - this.statusBarHeight)
			this.navbarWidth = menuButtonInfo.left;
			// #endif
			console.log(this.statusBarHeight)
		}
	}
</script>

<style lang="scss">
@import '../../common/css/icons.css';
.navbar-fixed {
	background-color: $mk-base-color;
	position: fixed;
	top: 0;
	left: 0;
	z-index: 99;
	width: 100%;
	.navbar-content {
		display: flex;
		justify-content: flex-start;
		align-items: center;
		// width: 100%;
		box-sizing: border-box;
		padding: 0 15px;
		// height: 45px;
		.navbar-search {
			padding: 0 10px;
			display: flex;
			align-items: center;
			height: 30px;
			width: 100%;
			background-color: #FFFFFF;
			border-radius: 30px;
			.navbar-search_icon {
				margin-right: 10px;
			}
			.navbar-search_text {
				font-size: 12px;
				color: #999;
			}
		}
	}
}
</style>
