<template>
	<view class="detailes">
		<u-sticky>
		<!-- 轮播 -->
		<view class="detaiLunBo">
			<u-swiper height="600" :list="list"></u-swiper>

		</view>

		<!-- 标题 -->
		<view class="detailTitle bcg">
			<h3>杨先生黑芝麻芡实糕八珍杨先生黑芝麻芡实糕八珍杨先生黑芝麻芡实糕八珍</h3>
		</view>

		<view class="bcg">
			<view class="deatilSY   btborder">
				<view class="deatil6">
					<view class="deatilList colorc4">
						<u-icon name="thumb-up-fill" size="40rpx" color="#ee8845"></u-icon>
						<view class="deatilListText">暂无数据</view>
					</view>
				</view>
				<view class="deatil6">
					<view class="deatilList colorc4">
						<u-icon name="play-circle-fill" size="40rpx" color="#ee8845"></u-icon>
						<view class="deatilListText">暂无数据</view>
					</view>
				</view>
				<view class="deatil6">
					<view class="deatilList colorc4">
						<u-icon name="minus-square-fill" size="40rpx" color="#ee8845"></u-icon>
						<view class="deatilListText">暂无数据</view>
					</view>
				</view>
			</view>
		</view>
		<view class="btn-de detailes">
			<view class="copy-url">
				<view>视频链接：111</view>
				<view class="copy-"> 复制 </view>
			</view>
			<view class="copy-Look">
				打开抖音查看
			</view>
			<view class="copy-ss">
				申诉
			</view>
<view class="sdrivier">
			<view class="sdrivier0"> </view>
			<view class="sdrivier1"> 其余接单达人 </view>
			<view class="sdrivier0"> </view>
		</view>
		</view>
		
		 
</u-sticky>
		<view class="sList row_s row_s_around" @click="navgetTo" v-for="(item,index) in 20" :key="index">
			<view class="">
				{{index+1}}
			</view>
			<view class="sListImg sic_logo">
				<image :src="logo" class="sk"></image>
			</view>
			<view class="sListCenter">
				<view class="sfw"> 金色悍马的推荐</view>
				<view class="ptb"></view>
				<view class="sfw"> 联系方式：139****8560</view>
			</view>
			<view class="bgcolor looks">
				查看
			</view>
		</view>


	</view>
</template>

<script>
	export default {


		data() {
			return {
				logo: require('../../static/images/mipmap-xhdpi/ic_logo.jpg'),
				list: [{
						image: 'https://cdn.uviewui.com/uview/swiper/1.jpg',
						title: '昨夜星辰昨夜风，画楼西畔桂堂东'
					} 
				]
			}
		},

		methods: {
			navgetTo() {
				uni.navigateTo({
					url: '/pages/dkdetail/merchantDetails'
				})
			},
			nativeGetTo() {
				uni.navigateBack()
			}
		},

	}
</script>

<style scoped lang="scss">
	.detailes{
		background-color: #fff;
		min-height: 100%;
	}
	.sList {
		padding: 20upx 0;
		border-bottom: 20upx solid #f5f5f5;
	}

	.ptb {
		padding: 10upx 0;
	}

	.sfw {
		font-weight: bold;
	}



	.HeaderLeftImg {
		width: 100upx;
		height: 100upx;
		margin-right: 40upx;
	}

	.row_s_around {
		justify-content: space-around;
	}

	.row_s_r {
		justify-content: space-between;
	}

	.row_s {
		display: flex;
		flex-direction: row;
		align-items: center;
	}

	.marginR {
		margin-right: 10upx;
	}

	.sfontWeight {
		font-weight: bold;
		font-size: 40upx;
		margin-bottom: 20upx;
	}

	.sdrivier {
		// width: 94%;
		margin: 40upx auto;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-around;
	}

	.sdrivier0 {
		flex: 1;
		height: 1px;
		background-color: #999;
	}

	.sdrivier1 {
		color: #999;
	}

	.sListImg {
		width: 120upx;
		height: 120upx;
		border-radius: 60upx;
		overflow: hidden;
	}

	.sic_logo .sk {
		width: 100%;
		height: 100%;
	}

	.copy-Look,
	.copy-ss {
		text-align: center;
		margin-top: 40upx;
		padding: 30upx 0;
		border-radius: 16upx;
	}

	.copy-Look {
		background-color: #7C75F5;
		color: #fff;
	}

	.copy-ss {
		background-color: #ee8845;
		color: #fff;
	}

	.btn-de {
		width: 100%;
		margin: 0 auto;
		padding: 0 4%;
	}

	.copy-url {
		display: flex;
		flex-direction: row;
		align-items: center;
		padding: 20upx;
		border: .5px solid #7C75F5;
		border-radius: 8px;
		justify-content: space-between;
	}

	.copy- {
		background-color: #7C75F5;
		color: #fff;
		padding: 10upx 20upx;
		border-radius: 10upx;
	}

	.detaiLunBo {
		position: relative;
	}

	.backImg {
		position: absolute;
		top: 30px;
		left: 20px;
		z-index: 99;
		background-color: #f5f5f5;
		width: 60upx;
		height: 60upx;
		line-height: 60upx;
		text-align: center;
		border-radius: 30upx;
	}

	.bcg {
		background-color: #fff;
	}

	.colorc4 {
		color: #999;
	}

	.colorc5 {
		color: #7C75F5;
	}

	.font20 {
		font-size: 20px;
	}

	.fontW {
		font-weight: bold;
	}

	.mt {
		margin-top: 20upx;
	}

	.detailTitle {
		padding: 40upx 40upx 0 40upx;
	}

	.deatilSY {
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;

		padding: 40upx;
	}

	.deatilSY0 {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.detailShare {}

	.btborder {
		width: 90%;
		margin: 0 auto;
		// border-top: .5px solid #c4c4c4;
	}

	.deatilList {
		display: flex;
		flex-direction: row;
		align-items: center;
	}

	.deatil6 {
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
		flex: 1;
	}

	.deatilListText {
		margin-left: 10upx;
	}

	.pdl {
		padding-left: 60upx;
	}

	.ptrb {
		padding: 40upx 0 40upx 0;
	}

	// 右侧title
	.item-title {
		position: relative;
		padding-left: 60upx;
		font-weight: bold;
	}


	.item-title:after {
		position: absolute;
		width: 12upx;
		height: 50upx;
		top: -8upx;
		content: "";
		left: 0;
		border-radius: 10px;
		background-color: #7C75F5;

	}

	.detailbaobei {
		padding: 40upx 20upx;

	}

	.detailbaobeiImg,
	.detailbaobeiImg image {
		width: 100%;
		display: flex;
		flex-direction: column;

	}

	.footerShare {
		height: 160upx;
		background-color: #333;
		position: fixed;
		bottom: 0;
		left: 0;
		right: 0;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-around;
	}

	.footerShare0 {
		flex: 1;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		color: #fff;
		font-size: 12px;
	}

	.footerShare1 {
		flex: 2;
		// background-color: red;
		color: #fff;
	}

	.footerShare11 {
		width: 100%;
		border-radius: 20%;
		padding: 14px 0;
	}

	.bacfff {
		border: 1px solid #fff;
	}

	.footerShare1 {

		width: 100%;
		border-radius: 50px;
		font-size: 26upx;
		text-align: center;
		margin-right: 10px;

	}

	.bacf5 {
		background-color: #7C75F5;
	}

	.footerShare2 {
		width: 100%;
		font-size: 12px;
		text-align: center;
		padding: 14px 0;

	}
	.bgcolor {
		background-color: #7C75F5;
		color: #fff;
	
	}
	.looks {
		padding: 10upx 30upx;
		border-radius: 10upx;
	}
</style>
