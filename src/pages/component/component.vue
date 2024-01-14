<template>
	<view class="container">
		<view class="desc">编译小程序时不支持使用 JS 文件导出 .vue 文件</view>
		<view class="box">
			<HelloWorld />
		</view>
	</view>
</template>

<script>
// import HelloWrold from '@/components/HelloWorld';
import HelloWorld from '@/components/HelloWorld/HelloWorld.vue';

export default {
	components: { HelloWorld }
}
</script>

<style>
.container {
	padding: 32rpx;
}
</style>
