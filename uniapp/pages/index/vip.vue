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
				<button @click="navigatorToLine" class="mission-r">我的</button>
			</view>
			<view class="mission-content-swiper">
				<u-swiper height="300" :list="list"></u-swiper>
			</view>
			<view class="mission-center">
				<view class="mission-center-center">
					<view class="center1  borderL1" @click="tabActive(item)" :class="current == index ?'bgcolor':''"
						v-for="(item,index) in listTabs" :key="index">
						{{item.name}}
					</view>

				</view> 
			</view>
		</view>
		<goodsList /> 
	</view>
</template>

<script>
	import {
		mapMutations,
		mapActions,
		mapState
	} from 'vuex';
	import goodsList from '../../components/juzheng/taskHallDetails/goodsList.vue';

	let systemInfo = uni.getSystemInfoSync();
	export default {
		components: {
			goodsList
		},
		data() {
			return {
				searchText: false,

				keyword: '',
				listTabs: [{
					name: '全部',
					id:0
				},{
					name: '智能家居',
					 id:1
				}, {
					name: "食品",
					id:2
				}],
				current: 0,
				list: [{
						image: 'https://cdn.uviewui.com/uview/swiper/1.jpg',
						title: '昨夜星辰昨夜风，画楼西畔桂堂东'
					},
					{
						image: 'https://cdn.uviewui.com/uview/swiper/2.jpg',
						title: '身无彩凤双飞翼，心有灵犀一点通'
					},
					{
						image: 'https://cdn.uviewui.com/uview/swiper/3.jpg',
						title: '谁念西风独自凉，萧萧黄叶闭疏窗，沉思往事立残阳'
					}
				]

			};
		},
		// 触底加载更多
		onReachBottom() {},
		onLoad() {},
		methods: {
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
					url:"/pages/dkdetail/rwOrder"
				})
				console.log("9999")
			},

		}

	};
</script>

<style lang="scss">
	.paddingTop20{
		padding-top: 20upx;
	}
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

	.mission-content-swiper {
		margin-top: 40upx;
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
		// height: 332upx;
		padding:80upx 20upx 60upx 20upx;
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

		.mission-l {
			width: 100%;
			position: relative;
		}

		/deep/ uni-button:after {
			border: none;
			outline: none;
		}

		.mission-r {
			width: 20%;
			height: 100upx;
			line-height: 100upx;
			font-size: 16px;
			background-color: #E7E5FB;
			border: none;
			outline: none;
			color: #7C75F5;

		}
	}
</style>
