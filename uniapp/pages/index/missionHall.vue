<!-- 商品列表 -->
<template>
	<view class="">
		<view class="mission-content">
			<view class="mission-c">
				<view class="mission-l">
					<u-search placeholder="搜索商品" shape="square" height="100" @custom="bandleSearch" :showAction="true"
						:animation="true" :clearabled="true" @confirm="confirmData" v-model="keyword"></u-search>
					<view class="mission-list" v-show="searchText">
						<view @click="searchTextList" class="mission-list-title"> 搜索的商品搜索的商品搜索的商品搜索的商品搜索的商品搜索的商品 </view>
						<view @click="searchTextList" class="mission-list-title"> 搜索的商品 </view>
						<view @click="searchTextList" class="mission-list-title"> 搜索的商品 </view>
					</view>
				</view>
				<button @click="navigatorToLine" class="mission-r">赚现金</button>
			</view>
			<!-- <view class="mission-center"> -->
			<!-- <u-tabs name="cate_name" count="cate_count" :list="list" :is-scroll="false" :current="current" @change="change" /> -->

			<!-- <view class="mission-center-center">
					<view class="center1  borderL1" @click="tabActive(item)" :class="current == index ?'bgcolor':''"  v-for="(item,index) in listTabs" :key="index">
						 {{item.name}}
					</view>
					 
				</view> -->
			<!-- <view  :class="countId==1 ? 'mission-t1':'mission-t2'"    @click="tabActive(item)"
					v-for="(item,index) in listTabs" :key="index">
					{{item.name}}
				</view> -->
			<!-- </view> -->
		</view>
		<goodsListVue @getCodeGoods="getCodeGoods" />
		<!-- 领取弹窗 -->
		<u-popup v-model="getShow" :borderRadius="10" mode="center" @close="close" @open="open">
			<view>
				<view class="modeReceive0">
					<view class="modeReceiveTitle"> 已领取，请联系客服～</view>
					<view class="modeReceiveTitle2">
					   <image :src="erweima" mode=""></image>
					</view>
					<view class="modeReceiveTitle3">
						保存到相册，微信扫一扫联系客服
					</view>
				</view>
			</view>
		</u-popup>
	</view>
</template>

<script>
	import {
		mapMutations,
		mapActions,
		mapState
	} from 'vuex';
	import goodsListVue from '../../components/juzheng/goodsList.vue';

	let systemInfo = uni.getSystemInfoSync();
	export default {
		components: {
			goodsListVue
		},
		data() {
			return {
				erweima:require('../../static/images/mine/erweima.png'),
				getShow: false, //领取弹窗
				searchText: false,
				countId: 1,
				keyword: '',
				listTabs: [{
					name: '直播任务',
					id: 0
				}, {
					name: "视频任务",
					id: 1
				}],
				current: 0

			};
		},
		// 触底加载更多
		onReachBottom() {},
		onLoad() {},
		methods: {
			close() {},
			open() {},
			getCodeGoods() {

				this.getShow = true
				console.log("uuuuuu", this.getShow)
			},
			change() {},
			// 点击收缩时触发
			bandleSearch() {
				this.searchText = !this.searchText
				console.log("----", this.keyword)
			},
			searchTextList() {
				this.searchText = !this.searchText
			},
			tabActive(item) {
				this.current = item.id
			},
			navigatorToLine() {
				uni.navigateTo({
					url: "/pages/dkdetail/rwOrder"
				})
				console.log("9999")
			},

		}

	};
</script>

<style lang="scss">
	.mission-center-center {
		width: 500upx;
		height: 100upx;
		margin: 0 auto;
		background-color: #f5f5f5;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
		border-radius: 50upx;

	}

	 

	.center1 {
		width: 250upx;
		height: 100upx;
		 
		text-align: center;
		line-height: 100upx;
		color: #999;
		font-size: 30upx;

	}

	.bgcolor {
		background-color: #7C75F5;
		color: #fff;

	}

	.borderL1 {
		border-radius: 50upx;
	}

	.mission-list {
		width: 100%;
		position: absolute;
		z-index: 88;
		background-color: #fff;
	}

	.mission-list-title {
		font-size: 16px;
		padding: 20upx;
	}

	.mission-content {
		padding: 40upx 20upx 60upx 20upx;
		background: linear-gradient(90deg, #F3E5F6, #E7E5FB);

		.mission-center {
			display: flex;
			flex-direction: row;
			align-items: center;
			justify-content: space-around;
			font-size: 18px;
			margin-top: 40upx;

			position: relative;

			.mission-t {
				color: #333;
			}
		}

		.c1 {
			color: #7C75F5;
		}

		.c2 {
			color: #333;
		}



		.mission-t1,
		.mission-t2 {
			color: #7C75F5;
		}

		.mission-t1::after {
			background: #7C75F5;
			color: #7C75F5;
			border-radius: 1px;
			position: absolute;
			bottom: -10px;
			content: "";
			height: 3px;
			left: 25%;
			position: absolute;
			-webkit-transform: translateX(-50%);
			-moz-transform: translateX(-50%);
			-o-transform: translateX(-50%);
			-ms-transform: translateX(-50%);
			transform: translateX(-50%);
			width: 35px;
		}

		.mission-t2::after {
			background: #7C75F5;
			color: #7C75F5;
			border-radius: 1px;
			position: absolute;
			bottom: -10px;
			content: "";
			height: 3px;
			left: 75%;
			position: absolute;
			-webkit-transform: translateX(-50%);
			-moz-transform: translateX(-50%);
			-o-transform: translateX(-50%);
			-ms-transform: translateX(-50%);
			transform: translateX(-50%);
			width: 35px;
		}
	}

	.mission-c {

		display: flex;
		flex-direction: row;
		padding: 0 20upx;
		padding-top: 60upx;

		.mission-l {
			width: 72%;
			margin-right: 15px;
			position: relative;
		}

		/deep/ uni-button:after {
			border: none;
			outline: none;
		}

		.mission-r {
			width: 27%;
			height: 100upx;
			line-height: 100upx;
			font-size: 16px;
			background-color: #E7E5FB;
			border: none;
			outline: none;
			color: #7C75F5;

		}
	}
	.modeReceive0 {
		// overflow: hidden;
		width: 600upx;
		border-radius: 18upx; 
		padding-bottom: 60upx;
	
	}
	
	.modeReceiveTitle {
		text-align: center;
	
		background-color: #9E8DDE;
		padding: 40upx 0;
		color: #fff;
		// border-top-left-radius: 20upx !important;
		// border-top-right-radius: 20upx !important;
	
	}
	
	.modeReceiveTitle2 {
		 
		width: 400upx;
		height: 400upx;
		margin: 0 auto;
		margin: 40upx auto;
		background-color: yellow;
	}
	.modeReceiveTitle2 image{
		width: 100%;
		height: 100%;
	}
	.modeReceiveTitle3{
		background: #363636;
		border-radius: 10px;
		color:#fff;
		font-size: 12px;
		width: 560upx;
		margin: 0 auto;
		padding: 8upx 0;
		text-align: center;
	}
</style>
