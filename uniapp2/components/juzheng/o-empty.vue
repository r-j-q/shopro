<template>
	<view :class="['o-empty']" :style="Bg">
		<image :style="ImgSize" :src="Img" mode="aspectFit"></image>
		<view class="text">{{text}}</view>
		<view class="slot" v-if="$slots.default"> <slot></slot> </view>
	</view>
</template>

<script>
	export default {
		name:'oEmpty',
		// #ifdef MP-WEIXIN
		options:{ virtualHost:true },
		// #endif
		props:{
			
			// img：缺省图片,可选值 error network search，支持传入图片URL
			// imgSize：缺省图尺寸,
			// text：描述文字,
			// bg：背景色
			
			img:{
				type:String,
				default:''
			},
			imgSize:{
				type:String,
				default:'320'
			},
			text:{
				type:String,
				default:'暂无数据'
			},
			bg:{
				type:String,
				default:'#fff'
			},
		},
		data() {
			return {
			Img:require('@/static/images/empty.svg')
			}
		},
		methods: {
			
		},
		computed: { 
		},
	}
</script>

<style lang="scss">
	.o-empty{
		min-height:380rpx;
		display: flex;
		flex-direction: column;
		padding: 64rpx 0!important;
		align-items: center;
		justify-content: center;
		box-sizing: border-box;
	}
	.center{text-align: center;}
	.text{
		color:#969798;
		padding: 20rpx 0;
	}
	.slot{
		padding-top: 20rpx;
	}
</style>
