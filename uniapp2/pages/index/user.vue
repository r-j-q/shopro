<!-- 个人中心 -->
<template>
	<view class="personal-wrap">
		<!-- 个人信息卡片 -->
		<userinfo-card v-if="userHeadData && userHeadData.style" :scrollTop="scrollTop" :detail="userHeadData"
			@onShare="onShare"></userinfo-card>
			<view class="vip_center">
				
			</view>
		<!-- 自定义模块 -->
		<!-- <view v-for="(item, index) in userTemplate" :key="item.id"> -->
		<!-- 轮播 -->
		<!-- 	<sh-banner
				v-if="item.type === 'banner' && index !== 0"
				:Px="item.content.x"
				:Py="item.content.y"
				:borderRadius="item.content.radius"
				:height="item.content.height"
				:list="item.content.list"
			></sh-banner> -->
		<!-- 滑动宫格 -->
		<!-- <sh-grid-swiper v-if="item.type === 'menu'" :list="item.content.list" :oneRowNum="item.content.style"></sh-grid-swiper> -->
		<!-- 广告魔方 -->
		<!-- <sh-adv v-if="item.type === 'adv'" :detail="item.content"></sh-adv> -->
		<!-- 推荐商品 -->
		<!-- <sh-hot-goods v-if="item.type === 'goods-list' || item.type === 'goods-group'" :detail="item.content"></sh-hot-goods> -->
		<!-- 富文本 -->
		<!-- <sh-richtext v-if="item.type === 'rich-text'" :richId="item.content.id"></sh-richtext> -->
		<!-- 功能列表 -->

		<!-- <sh-cell v-if="item.type === 'nav-list'" :list="item.content.list"></sh-cell> -->
		<!-- 九宫格列表 -->
		<!-- <sh-grid v-if="item.type === 'grid-list'" :list="item.content.list"></sh-grid> -->
		<!-- 钱包 -->
		<!-- <sh-wallet v-if="item.type === 'wallet-card'"></sh-wallet> -->
		<!-- 订单卡片 -->
		<!-- <sh-order-card v-if="item.type === 'order-card'"></sh-order-card> -->
		<!-- </view> -->

		<!-- <sh-cell   :list="itemContentList"></sh-cell> -->
		<view class="order_dingdang mt50">
			<view class="order_dingdang_left1">
				<view class="order_dingdang_weit">
				10000	
				</view>
				<view class="order_dingdang_left_text1">
				 冻结金额	
				</view>
			</view>
			<view class="order_dingdang_right1">
				<view class="order_dingdang_weit">
				12000	
				</view>
				<view class="order_dingdang_right_text1">
				 积分	
				</view>
			</view>
		</view>
		<view class="order_dingdang">
			<view class="order_dingdang_left">
				 
				<view class="order_dingdang_left_text">
				 积分订单	
				</view>
			</view>
			<view class="order_dingdang_right">
				 
				<view class="order_dingdang_right_text">
				 任务订单	
				</view>
			</view>
		</view>
		<sh-grid :list="itemContentList"></sh-grid>
		<!-- copyright -->
		<!-- <view class="copyright-box u-flex-col u-row-center u-col-center u-p-t-80 u-p-b-50" v-if="initShop.copyright">
			<view class="copyright-text">{{ initShop.copyright[0] }}</view>
			<view class="copyright-text">{{ initShop.copyright[1] }}</view>
		</view> -->

		<!-- #ifdef H5 -->
		<view class="tabbar-hack" style="height: 120rpx; width:100%;"></view>
		<!-- #endif -->
		<!-- 关注弹窗 -->
		<!-- <shopro-float-btn></shopro-float-btn> -->
		<!-- 登录提示 -->
		<shopro-auth-modal></shopro-auth-modal>
		<!-- 分享组件 -->
		<shopro-share v-model="showShare" posterType="user"></shopro-share>
		<!-- <shopro-tabbar></shopro-tabbar> -->
	</view>
</template>

<script>
	import shBanner from './components/sh-banner.vue';
	import shGridSwiper from './components/sh-grid-swiper.vue';
	import shAdv from './components/sh-adv.vue';
	import shRichtext from './components/sh-richtext.vue';
	import shCell from './components/sh-cell.vue';
	import shGrid from './components/sh-grid.vue';
	// import shOrderCard from './componentsA/sh-order-card.vue';
	import shWallet from './components/sh-wallet.vue';
	import shHotGoods from './components/sh-hot-goods.vue';

	import userinfoCard from './user/userinfo-card.vue';

	import {
		mapMutations,
		mapActions,
		mapState,
		mapGetters
	} from 'vuex';

	import share from '@/shopro/share';

	export default {
		components: {
			shBanner,
			shGridSwiper,
			shAdv,
			shRichtext,
			shCell,
			shGrid,
			shWallet,
			// shOrderCard,
			shHotGoods,

			userinfoCard
		},
		data() {
			return {
				scrollTop: 0,
				showShare: false,
				enable: false, //是否开启吸顶。
				itemContentList: [{
						name: "个人信息",
						image: require("../../static/images/mipmap-xhdpi/ic_gerenxinxi.webp")
					},
					{
						name: "增值服务",
						image: require("../../static/images/mipmap-xhdpi/ic_mine_service.webp")
					},
					{
						name: "联系客服",
						image: require("../../static/images/mipmap-xhdpi/ic_lianxikefu.webp")
					},
					{
						name: "订单",
						image: require("../../static/images/mipmap-xhdpi/ic_dingdan.webp")
					},
					{
						name: "课程中心",
						image: require("../../static/images/mipmap-xhdpi/ic_xuexizhongxin.webp")
					},
					{
						name: "学员兑换",
						image: require("../../static/images/mipmap-xhdpi/ic_xueyuanduihuan.webp")
					},
					{
						name: "推广中心",
						image: require("../../static/images/mipmap-xhdpi/ic_tuiguangzhongxin.webp")
					},
					{
						name: "收藏",
						image: require("../../static/images/mipmap-xhdpi/ic_mine_shoucang.webp")
					},
				]
			};
		},
		computed: {
			...mapGetters(['initShop', 'userTemplate', 'isLogin', 'userInfo', 'authType']),
			userHeadData() {
				if (this.userTemplate?.length) {
					return this.userTemplate[0].content;
				}
			}
		},
		// 下拉刷新
		onPullDownRefresh() {
			this.init();
		},
		onPageScroll(e) {
			this.scrollTop = e.scrollTop;
		},

		onShow() {
			if (this.isLogin) {
				this.init();
				this.getUserData();
			}
			this.enable = true;
		},

		methods: {
			...mapActions(['getUserInfo', 'showAuthModal', 'getUserData']),
			onShare() {
				this.showShare = true;
				uni.hideTabBar();
			},
			// 初始化
			init() {
				this.getUserInfo()
					.then(res => {
						uni.stopPullDownRefresh();
					})
					.catch(e => {
						uni.stopPullDownRefresh();
					});
			}
		}
	};
</script>

<style lang="scss" scoped>
	.mt50{
		margin-top: 180rpx;
	}
	.personal-wrap{
		min-height: 100%;
		background-color: #fff;
	}
	.order_dingdang_weit{
		font-size: 50upx;
		color: #333;
		font-weight: bold;
	}
	.order_dingdang {
		background-color: #fff;
		padding: 40upx;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
	}
.order_dingdang_left1 {
		width: 50%;
		margin-right: 10upx;
		height: 140upx;
		border-radius: 8upx;
		 display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		 
	}

	.order_dingdang_right1 {
		width: 50%;
		height: 140upx;
		margin-left: 10upx;
		border-radius: 8upx; 
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		 
	}
	.order_dingdang_left {
		width: 50%;
		margin-right: 10upx;
		height: 140upx;
		border-radius: 8upx; 
		background-image:url('../../static/images/mipmap-xhdpi/ic_jifenduihuan.webp') ;
		background-size: cover;
		background-repeat: no-repeat;
	}

	.order_dingdang_right {
		width: 50%;
		height: 140upx;
		margin-left: 10upx;
		border-radius: 8upx; 
		background-image:url('../../static/images/mipmap-xhdpi/ic_renwudating.webp') ;
		background-size: cover;
		background-repeat: no-repeat;
	}
	.order_dingdang_left_text1{ font-size: 28upx;}
	.order_dingdang_right_text1{ font-size: 28upx;}
     .order_dingdang_left_text{
		 font-weight: bold;
		 font-size: 36upx;
		 margin: 50upx 20upx;
	 }
	 .order_dingdang_right_text{
		 font-weight: bold;
		 font-size: 36upx;
		 margin: 50upx 20upx;
	 }
	.copyright-box {
		.copyright-text {
			font-size: 22rpx;
			font-weight: 500;
			color: #c4c4c4;
		}
	}
	  .u-flex {
		width: 100%!important;
	}
</style>
