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
				<button @click="navigatorToLine" class="mission-r">赚元宝</button>
			</view>
			<view class="mission-content-swiper">
				<u-swiper height="300" :list="list"></u-swiper>
			</view>
			<view class="mission-center">
				 <shType @handleShowMore="handleShowMore"/>
				 
			</view>
		</view>
		<shTypeBtn/>
		<goodsList /> 
		
		<!-- 领取弹窗 -->
		<u-popup v-model="isHandleShowMore" :borderRadius="0" mode="top" >
			<view class="isHandleShowMorePadding">
				 <shTypeBtn/>
				 <view class="isMorePaddingList">
				 	<view @click.stop="getIsMorePaddingList(flag)" class="isMorePstyle" :class="flag.id==typeId?'isMoreBackground':''" v-for="(flag,i) in listTabs" :key="i">{{flag.name}}</view>
				 	 
				 </view>
				 <view class="isMorePaddingBottom">
				 	<view class="isMorePaddingBottom0">
				 		重置
				 	</view>
					<view class="isMorePaddingBottom1">
						完成
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
	import goodsList from '../../components/juzheng/taskHallDetails/goodsList.vue';
	import shType from '../../components/juzheng/taskHallDetails/sh-type.vue';
	import shTypeBtn from '../../components/juzheng/taskHallDetails/sh-type-btn.vue';
 
	let systemInfo = uni.getSystemInfoSync();
	export default {
		components: {
			goodsList,
			shType,
			shTypeBtn
		},
		data() {
			return {
				isHandleShowMore:false,//更多类型弹窗
				searchText: false,

				keyword: '',
				typeId:0,//更多类型ID
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
			 
			navigatorToLine() {
				uni.navigateTo({
					url:"/pages/dkdetail/rwOrder"
				})
				console.log("9999")
			},
			//显示更多类型
			handleShowMore(){
				this.isHandleShowMore= ! this.isHandleShowMore
			},
			// 点击更多类型
			getIsMorePaddingList(v){
				 this.typeId = v.id
			}
            
		}

	};
</script>

<style lang="scss">
	.paddingTop20{
		padding-top: 20upx;
	}
	  

	.mission-content-swiper {
		margin-top: 40upx;
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
		padding:80upx 20upx 24upx 20upx;
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
			width: 77%;
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
	// 弹窗里面筛选内容
	.isHandleShowMorePadding{
		padding: 40upx;
	}
	.isMorePaddingList{
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
		flex-wrap: wrap;
		width: 100%;
		margin-top: 20upx;
		padding-top: 20upx;
		border-top: 1px solid #f5f5f5;
	}
	.isMorePstyle{
		background-color: #f5f5f5;
		color: #000;
		font-size: 26upx;
		padding: 14upx 40upx;
		margin-bottom: 20upx;
		border-radius: 8upx;
	}
	.isMorePaddingBottom{
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
		margin-top: 60upx;
	}
	.isMorePaddingBottom0{
		font-size: 26upx;
		color: #333;
		border-radius: 16upx;
		width: 48%;
		background-color: #f5f5f5;
		text-align: center;
		padding: 20upx 0;
	}
	.isMorePaddingBottom1{
		font-size: 26upx;
		font-size: 26upx;
		background-color: #7C75F5;
		border-radius: 16upx;
		color: #fff;
		width: 48%;
		text-align: center;
		padding: 20upx 0;
		
	}
	.isMoreBackground{
		background-color: #E7E5FB;
		color: #7C75F5;
	}
</style>
