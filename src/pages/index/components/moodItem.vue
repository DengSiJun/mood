<template>
	<view class="container">
		<view class="bar" :class="[{current: item.isCurrent, active: active}, pointLevel]" :style="{height: data.point  * barHeightUnit + 'rpx'}">
			<text class="point">{{item.point || ''}}</text>
			<image :src="imageURL"></image>
		</view>
		<view class="day" :class="[{current: item.isCurrent, active: active}, pointLevel]">
			{{data.day}}
		</view>
	</view>
</template>

<script>
	export default {
		props: ['item', 'active'],
		data() {
			return {
				barHeightUnit: 5.5,
				data: {
					point: 0,
					day: ''
				},
				imageURL: ''
			}
		},
		mounted() {
			setTimeout(() => {
				this.data.point = this.item.point || 30
				this.data.day = this.item.day
				this.setImageURL()
			}, this.item.index * 100)
		},
		computed: {
			pointLevel() {
				let point = this.item.point || 0
				if (point >= 90) {
					return 'good'
				} else if (point >= 50) {
					return 'normal'
				}
				return 'default'
			}
		},
		methods: {
			setImageURL() {
				this.imageURL = '/static/icon_' + this.pointLevel + (this.active ? '_active' : '') + '.svg'
			}
		},
		watch: {
			active: function() {
				this.setImageURL()
			}
		}
	}
</script>

<style scoped>
	.container {
		position: relative;
		display: flex;
		justify-content: center;
	}
	
	.bar {
		position: absolute;
		bottom: 80rpx;
		width: 80rpx;
		background: #CFCFCF;
		border-radius: 50rpx;
		display: flex;
		justify-content: center;
		transition: height 0.3s;
	}
	
	.bar .point {
		color: #fff;
		font-family: 'Nunito';
		font-style: normal;
		font-weight: 700;
		font-size: 36rpx;
		margin-top: 20rpx;
	}
	
	.bar image {
		width: 70rpx;
		height: 70rpx;
		position: absolute;
		bottom: 10rpx;
	}
	
	.bar.normal {
		background: #52C873;
	}
	
	.bar.good {
		background: #FF823C;
	}
	
	.bar.active {
		width: 90rpx;
		box-shadow: 0rpx 8rpx 20rpx rgba(0, 0, 0, 0.15);
		border-radius: 60rpx;
	}
	
	.bar.active.normal {
		background: linear-gradient(180deg, #42F373 42.71%, #A1FD44 100%);
		border: 6rpx solid #DCFFD6;
		
	}
	
	.bar.active.good {
		background: linear-gradient(180deg, #FFA14A 35.42%, #FFCC4A 100%);
		border: 6rpx solid #FFE9D5;
	}
	
	.day {
		position: absolute;
		bottom: 0;
		color: #2D2F33;
		font-weight: 500;
		font-size: 32rpx;
		width: 66rpx;
		height: 66rpx;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	
	.day.current {
		color: #fff;
		background: #2D2F33;
		border-radius: 12rpx;
	}
	
	.day.active {
		color: #2D2F33;
		background: #FFFFFF;
		box-shadow: 0rpx 8rpx 20rpx rgba(0, 0, 0, 0.2);
		border-radius: 12rpx;
	}
	
	.day.active {
		color: #2D2F33;
	}
	
	.day.active.normal {
		color: #52C873;
	}
	
	.day.active.good {
		color: #FF823C;
	}
</style>