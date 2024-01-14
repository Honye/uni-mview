<template>
	<view class="text-center container">
		<image class="logo" src="/static/logo.png" />
		<view>uni-app 开发常见问题和注意事项</view>
		<view class="mt-4 nav-list">
			<navigator
				v-for="item in navList"
				class="nav-item"
				:class="{ 'nav-item-deprecated': item.deprecated }"
				:key="item.path"
				:url="item.path"
			>{{ item.title }}</navigator>
		</view>
		<view class="absolute bottom-0 left-0 right-0 pb-safe">
			<view class="text-xs text-gray-400">源码：Honye/uni-mview</view>
		</view>
	</view>
</template>

<script>
export default {
	data: () => ({
		navList: [
			{
				path: '/pages/component/component',
				title: '组件引用路径（Vite + Vue3 正常）',
				deprecated: true
			},
			{
				path: '/pages/request/request',
				title: '请求参数处理'
			},
			{
				path: '/pages/style/style',
				title: '样式处理'
			}
		]
	})
}
</script>

<style>
.logo {
	display: block;
	height: 160rpx;
	width: 160rpx;
	margin-top: 100rpx;
	margin-left: auto;
	margin-right: auto;
	margin-bottom: 50rpx;
}
.nav-item {
	font-size: 32rpx;
	line-height: 2;
	color: rgb(59 130 246);
	text-decoration: underline;
	text-align: center;
}
.nav-item-deprecated {
	text-decoration: line-through;
}
</style>
