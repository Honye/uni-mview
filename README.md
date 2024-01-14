# uni-app 问题记录

## H5 和微信小程序请求参数处理的区别

发起 GET 请求时对数组类型的参数处理方式不同

H5：数组类型参数会隐式转换为 `string` 类型。如：`[123, 456]` 会转为 `'123,456'`
微信小程序：数组参数为转为 JSON 字符。如：`['123', '456']` 会转为 `'["123","456"]'`

## H5 和微信小程序样式处理区别

编译 H5 应用时 uni-app 会自动给 style 添加 scoped。开发中应尽量不给 style 添加 scoped，避免样式难以覆盖

微信小程序中样式隔离（`styleIsolation`）策略默认使用的是 `apply-shared`。页面样式会影响组件样式

## H5 和微信小程序自定义组件样式区别

自定义组件上添加 `class` 修改样式，在微信小程序中不生效，在 H5 中正常

```xml
<!-- /src/components/StyledText.vue -->
<template>
	<text class="text"><slot /></text>
</template>

<style>
.text {
	font-szie: 36rpx;
	color: #222;
}
</stye>
```

```xml
<template>
	<view>
		<StyledText class="text-red-500" />这段文本在 H5 中是红色，在小程序中却呈现黑色</StyledText>
	</view>
</template>

<script setup>
import StyledText from '@/components/StyledText.vue';
</script>

<style>
.text-red-500 {
	color: rgb(239 68 68);
}
</style>
```

解决方案：为了良好的兼容性，禁止在自定义组件添加 class。若要修改覆盖自定义组件样式可在父级元素添加 class 然后使用 css 父子选择器修改样式

```xml
<template>
	<view class="parent">
		<StyledText>这段文本在 H5 中是红色，在小程序中却呈现黑色</StyledText>
	</view>
</template>

<script setup>
import StyledText from '@/components/StyledText.vue';
</script>

<style>
.parent .text {
	color: rgb(239 68 68);
}
</style>
```

## H5 和微信小程序组件引用路径区别

H5 自定义组件可以使用 index.js 作为导出，微信小程序不能

```js
// /src/components/HelloWorld/index.js
export { default } from './HelloWorld.vue';
```

```js
// 下面一行代码编译异常
import HelloWorld from '@/components/HelloWorld';
// 注释上面一行后取消注释下面一行可正常使用
// import HelloWorld from '@/components/HelloWorld/HelloWorld.vue';
```
