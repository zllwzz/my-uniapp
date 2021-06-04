<template>
	<view class="tab">
		<scroll-view class="tab-scroll" scroll-x>
			<view class="tab-scroll__box">
				<view class="tab-scroll__item" v-for="(item, index) in list" :key="item._id" @click="clickTab(item, index)" :class="{active: activeIndex === index}">
					{{item.name}}
				</view>
			</view>
		</scroll-view>
		<view class="tab-icons">
			<uni-icons type="gear" size="26" color="#666"></uni-icons>
		</view>
	</view>
</template>

<script>
	export default {
		name:"tab",
		props: {
			list: {
				type: Array,
				default: () => []
			}
		},
		data() {
			return {
				activeIndex: ''
			};
		},
		methods: {
			clickTab(item, index) {
				this.activeIndex = index;
				this.$emit('tab', {
					data: item,
					index
				})
			}
		}
	}
</script>

<style lang="scss">
.tab {
	display: flex;
	border-bottom: 1px solid #f5f5f5;
	width:100%;
	background-color: #fff;
	box-sizing: border-box;
	.tab-scroll {
		flex:1;
		overflow: hidden;
		.tab-scroll__box {
			display: flex;
			height: 45px;
			align-items: center;
			flex-wrap: nowrap;
			box-sizing: border-box;
			.tab-scroll__item {
				flex-shrink: 0;
				padding: 0 10px;
				font-size: 14px;
				color:#333;
				&.active {
					color: $mk-base-color;
				}
			}
		}
	}
	.tab-icons {
		position: relative;
		flex-basis: 45px;
		display: flex;
		justify-content: center;
		align-items: center;
		&::before {
			content: '';
			position: absolute;
			top:12px;
			bottom:12px;
			left:0;
			width:1px;
			background: #ddd;
		}
	}
}
</style>
