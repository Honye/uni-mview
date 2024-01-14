<template>
	<view class="container">
		<view class="desc">
			<view>自定义组件上添加 class 修改样式在 H5 中和微信小程序中有不同的表现</view>
			<view><text class="font-semibold">H5：</text>有效</view>
			<view><text class="font-semibold">微信小程序：</text>无效</view>
		</view>
		<view class="box">
			<StyledText class="text-red-500">这段文本在 H5 中是红色，在小程序中却呈现黑色</StyledText>
		</view>
	</view>
</template>

<script>
import StyledText from '@/components/StyledText.vue';

export default {
	components: { StyledText }
}
</script>

<style>
.container {
	padding: 32rpx;
}
.text-red-500 {
	color: rgb(239 68 68);
}
</style>
