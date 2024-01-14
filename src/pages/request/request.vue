<template>
  <view class="container">
		<view class="desc">
			<view><text class="font-semibold">H5：</text>GET 请求参数默认隐式转为 string 类型</view>
			<view><text class="font-semibold">微信小程序：</text>GET 请求参数默认使用 JSON 序列化转为 string</view>
			<view>注意观察参数 <text class="font-semibold">emptyArr</text> 和 <text class="font-semibold">arr</text> 在 H5 和微信小程序中的区别</view>
		</view>
		<button class="mt-4" type="primary" @tap="requestGET">发起 GET 请求</button>
		<view class="box json-viewer">
			<!-- #ifdef H5 -->
			打开 DevTools 查看请求参数
			<!-- #endif -->
			<!-- #ifndef H5 -->
			{{ jsonData }}
			<!-- #endif -->
		</view>
  </view>
</template>

<script>
const params = {
	str: 'Hello',
	num: 123,
	bool: true,
	emptyArr: [],
	arr: ['123', '456']
};

export default {
	data: () => ({
		jsonData: ''
	}),
	methods: {
		async requestGET() {
			const { data } = await uni.request({
				url: 'https://postman-echo.com/get',
				method: 'GET',
				data: params
			});
			this.jsonData = JSON.stringify(data, null, 4);
		}
	}
}
</script>

<style>
.container {
	padding: 32rpx;
}
.desc {
	line-height: 1.6;
}
.mt-4 {
	margin-top: 1rem;
}
.json-viewer {
	min-height: 200rpx;
	white-space: pre;
	overflow-x: auto;
}
</style>
