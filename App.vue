<script>
export default {
	onLaunch: function () {
		console.log('App Launch')
	},
	onShow: function () {
		console.log('App Show')
	},
	onHide: function () {
		console.log('App Hide')
	}
}
</script>

<style lang="less">
/*每个页面公共css */
@font-face {
	font-family: 'iconfont-other';
	/* Project id 4846774 */
	src: url('https://at.alicdn.com/t/c/font_4846774_5ne0tj6989s.woff2?t=1743672868084') format('woff2'),
		url('https://at.alicdn.com/t/c/font_4846774_5ne0tj6989s.woff?t=1743672868084') format('woff'),
		url('https://at.alicdn.com/t/c/font_4846774_5ne0tj6989s.ttf?t=1743672868084') format('truetype');
}

@font-face {
	font-family: 'iconfont-class';
	/* Project id 4846774 */
	src: url('https://at.alicdn.com/t/c/font_4846761_id0q2fy6p6l.woff2?t=1743408662408') format('woff2'),
		url('https://at.alicdn.com/t/c/font_4846761_id0q2fy6p6l.woff?t=1743408662408') format('woff'),
		url('https://at.alicdn.com/t/c/font_4846761_id0q2fy6p6l.ttf?t=1743408662408') format('truetype');
}
/* 隐藏浏览器滚动条 */
::-webkit-scrollbar {
	display: none;
}
html, body {
	scrollbar-width: none; /* Firefox */
	-ms-overflow-style: none; /* IE 10+ */
}
</style>
