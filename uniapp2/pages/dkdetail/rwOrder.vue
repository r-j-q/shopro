<template>
	<view class="bac100">
		<view class="mission-center">
			<view class="mission-center-center">
				<view class="center1  borderL1" @click="tabActive(item)" :class="current == index ?'bgcolor':''"
					v-for="(item,index) in listTabs" :key="index">
					{{item.name}}
				</view>

			</view>
		</view>
		<view class="">
			<view class="">
				<OEmpty />
				<button class="backIndex" @click="goIndex">去首页</button>
			</view>
		</view>

	</view>
</template>

<script>
	import OEmpty from "@/components/juzheng/o-empty.vue"
	export default {

		components: {
			OEmpty
		},
		data() {
			return {
				listTabs: [{
					name: '全部',
					value:0,
					id: 0
				}, {
					name: '待完成',
					value:1,
					id: 1
				}, {
					name: "进行中",
					value:0,
					id: 2
				}, {
					name: "未通过",
					value:0,
					id: 3
				}, {
					name: "已完成",
					value:2,
					id: 4
				}, {
					name: "已取消",
					value:0,
					id: 5
				}],
				current: 0,
			}
		},

		methods: {
			tabActive(item) {
				this.current = item.id
			},
			goIndex() {
				uni.switchTab({
					url: "/pages/index/index"
				})
			}
		},

	}
</script>

<style scoped lang="scss">
	.bac100 {
		background-color: #fff;
		min-height: 100%;
	}

	.backIndex {
		width: 30%;
		margin: 0 auto;
		color: #fff;
		background-color: #7C75F5;
		border: none;
	}

	.mission-center {
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-around;
		font-size: 18px;
		background-color: #fff;
		padding: 40upx 20upx;
		position: relative;


	}

	.mission-center-center {
		width: 100%;
		height: 80upx;
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
		height: 80upx;
		text-align: center;
		line-height: 80upx;
		color: #999;
		font-size: 30upx;

	}

	.borderL1 {
		border-radius: 50upx;
	}

	.bgcolor {
		background-color: #7C75F5;
		color: #fff;

	}
</style>
