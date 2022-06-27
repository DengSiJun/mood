<template>
	<view class="container">
		<!-- Status Bar -->
		<view class="status_bar"></view>
		<!-- Navigation Bar -->
		<view class="navigation_bar">
			<view class="left" @click="back">
				<image src="/static/back.svg" class="back"></image>
			</view>
			<view class="title">历史心情指数</view>
		</view>
		<!-- Main content -->
		<view class="main">
			<view class="card">
				<view class="user">
					<image :src="user.avatar"></image>
					<text>{{user.name || '姓名'}}</text>
				</view>
				<view class="point">{{avgPoint}}</view>
				<view class="desc">周平均心情指数</view>
			</view>
			<mood-chart :data="data"></mood-chart>
		</view>
	</view>
</template>

<script>
	import moodChart from './components/moodChart.vue'
	
	export default {
		components: {
			moodChart
		},
		data() {
			return {
				user: {
					avatar: '/static/avatar.svg',
					name: '李强'
				},
				data: [
					{index: 1, day: '六', point: 86},
					{index: 2, day: '日', point: 80},
					{index: 3, day: '一'},
					{index: 4, day: '二', point: 90},
					{index: 5, day: '三', point: 92},
					{index: 6, day: '四', point: 97},
					{index: 7, day: '五', point: 81, isCurrent: true},
				]
			}
		},
		methods: {
			back() {
				uni.navigateBack()
			}
		},
		computed: {
			avgPoint() {
				if (!this.data || this.data.length === 0) {
					return 0
				}
				let sum = 0
				let length = this.data.length
				for (let i = 0; i < this.data.length; i++) {
					let point = this.data[i].point || 0
					if (point <= 0) {
						length--
						continue
					}
					sum += point
				}
				return Math.ceil(sum / length)
			}
		}
	}
</script>

<style scoped>
	.status_bar {
		height: var(--status-bar-height);
		width: 100%;
	}
	
	.main {
		padding: 0 24rpx;
	}
	
	.main .card {
		display: flex;
		justify-content: center;
		flex-direction: column;
		align-items: center;
		width: 100%;
		height: 476rpx;
		background: #FFFFFF;
		box-shadow: 0rpx -6rpx 16rpx 0 rgba(0, 0, 0, 0.15);
		border-radius: 48rpx 48rpx 0 0;
	}
	
	.main .card .user {
		font-weight: 500;
		font-size: 36rpx;
		display: flex;
		align-items: center;
	}
	
	.main .card .user image {
		width: 60rpx;
		height: 60rpx;
		border-radius: 50%;
		margin-right: 20rpx;
	}
	
	.main .card .point {
		font-weight: 800;
		font-size: 130rpx;
		letter-spacing: -0.6rpx;
		line-height: 200rpx;
	}
	
	.main .card .desc {
		font-weight: 500;
		font-size: 32rpx;
		color: #929292;
	}
</style>
