<template>
	<view class="container">
		<view class="chart">
			<mood-item v-for="item in data" :item="item" :key="item.index" :active="item.index === activeIndex"
				@click.native="onItemClick(item.index)"></mood-item>
		</view>
		<view class="line top"></view>
		<view class="line middle"></view>
	</view>

</template>

<script>
	import moodItem from './moodItem.vue'

	export default {
		components: {
			moodItem
		},
		props: ['data'],
		data() {
			return {
				activeIndex: -1
			}
		},
		methods: {
			onItemClick(index) {
				this.activeIndex = this.activeIndex === index ? -1 : index
			}
		}
	}
</script>

<style scoped>
	.container {
		position: relative;
		width: 100%;
	}

	.chart {
		height: 630rpx;
		display: flex;
		justify-content: space-between;
	}

	.line {
		background: #F2F2F2;
		height: 4rpx;
		z-index: -1;
	}

	.top {
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
	}

	.middle {
		position: absolute;
		top: 250rpx;
		left: 0;
		right: 0;
	}
</style>
