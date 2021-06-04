<template>
	<view class="home">
		<navbar></navbar>
		<tab :list="tabList" @tab="tab"></tab>
		<view class="scroll">
			<scroll-view class="list-scroll" scroll-y>
				<view class="">
					<view v-for="(item,index) in 100" :key="index">
						{{item}}
					</view>
				</view>
			</scroll-view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				tabList: []
			}
		},
		onLoad() {
			this.getLabel()
		},
		methods: {
			tab({data,index}){
				console.log(data,index)
			},
			getLabel() {
				this.$api.get_label({}).then(res => {
					this.tabList = res.data
				})
			}
		}
	}
</script>

<style lang="scss">
page {
	height: 100%;
	display: flex;
}
.home {
	display: flex;
	flex-direction: column;
	flex: 1;
	.scroll {
		flex: 1;
		overflow: hidden;
		// box-sizing: border-box;
		.list-scroll {
			height: 100%;
			display: flex;
			flex-direction: column;
		}
	}
}
</style>
