<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
	.status_bar {
		height: var(--status-bar-height);
		width: 100%;
	}
	
	.navigation_bar {
		position: relative;
		height: 120rpx;
		line-height: 100rpx;
		width: 100%;
		display: flex;
		justify-content: center;
	}
	
	.navigation_bar .left {
		position: absolute;
		left: 40rpx;
	}
	
	.navigation_bar .back {
		width: 47rpx;
		height: 34rpx;
	}
	
	.navigation_bar .title {
		color: #2D2F33;
		font-size: 36rpx;
		font-weight: 500;
		text-align: center;
		overflow: hidden;
		white-space: nowrap;
		text-overflow: ellipsis;
	}
	
	.container {
		font-family: 'PingFang HK';
	}
</style>
