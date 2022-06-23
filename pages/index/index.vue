<template>
	<view class="content">
		<image class="logo" src="/static/heart.jpeg" mode="aspectFill"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
		<view class="mood">
			<button @click="onMoodClick">历史心情指数</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {
			onMoodClick() {
				uni.navigateTo({
					url: './mood'
				})
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
	
	.mood {
		margin-top: 100rpx;
	}
	
	.mood button {
		font-size: 30rpx;
	}
</style>
