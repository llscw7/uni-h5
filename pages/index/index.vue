<template>
	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{ title }}</text>
		</view>
	</view>
	<view style="width: 750rpx ;height: 750rpx;">
		<l-signature disableScroll ref="signatureRef" :penColor="penColor" :penSize="penSize"
			:openSmooth="openSmooth"></l-signature>
	</view>
	<view>
		<button @click="onClick('clear')">清空</button>
		<button @click="onClick('undo')">撤消</button>
		<button @click="onClick('save')">保存</button>
		<!-- uvue 不支持 openSmooth -->
		<button @click="onClick('openSmooth')">压感{{ openSmooth ? '开' : '关' }}</button>
	</view>
</template>

<script>
import dayjs from 'dayjs'
export default {
	data() {
		return {
			title: 'Hello',
			penColor: 'red',
			penSize: 5,
			url: '',
			openSmooth: true
		}
	},
	onLoad() {
		// 获取当前时间
		const currentTime = dayjs().format('YYYY-MM-DD HH:mm:ss')
		// 设置标题
		this.title = `当前时间: ${currentTime}`
		console.log(currentTime, '======')
	},
	methods: {
		onClick(type) {
			if (type == 'openSmooth') {
				this.openSmooth = !this.openSmooth
				return
			}
			if (type == 'save') {
				this.$refs.signatureRef.canvasToTempFilePath({
					success: (res) => {
						// 是否为空画板 无签名
						console.log(res.isEmpty)
						// 生成图片的临时路径
						// H5 生成的是base64
						this.url = res.tempFilePath
					}
				})
				return
			}
			if (this.$refs.signatureRef)
				this.$refs.signatureRef[type]()
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
</style>
