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
@import '@/styles/common.scss';

page {
	color: #333;
}
button[type=primary] {
	background-color: rgb(13 148 136);
}
.button-hover[type=primary] {
	background-color: rgb(15 118 110);
}

.box {
	margin-block: 32rpx;
	border: 1px solid rgb(156 163 175);
	border-radius: 16rpx;
	padding: 16rpx;
}
</style>
