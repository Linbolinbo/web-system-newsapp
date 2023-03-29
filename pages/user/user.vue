<template>
	<view class="user">
		<view class="top">
			<image src="../../static/images/history.png" mode=""></image>
			<view class="text">浏览历史</view>
		</view>
		<view class="content">
			<view class="row" v-for="item in listArr" >
				<newsbox :item="item" @click.native="goDetail(item)"></newsbox>
				</view>
		</view>
		<view class="nohistory" v-if="!listArr.length">
			<image src="../../static/images/nodata.png" mode="widthFix"></image>
			<view class="text">
				暂无浏览记录
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				listArr:[]
			};
		},
		onShow() {
			this.getData()
		},
		methods:{
			goDetail(item){
				uni.navigateTo({
					url:`/pages/detail/detail?cid=${item.classid}&id=${item.id}`
				})
			},
			getData(){
				let hisArr=uni.getStorageSync("historyArr") || []
				this.listArr=hisArr
				console.log(this.listArr);
			}
			
		}
	}
</script>

<style lang="scss">
.user{
	.top{
		background: #f8f8f8;
		padding:50rpx 0;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		image{
			width: 120rpx;
			height: 120rpx;
		}
		.title{
			font-size: 38rpx;
			color:#666;
			padding-top:30rpx;
		}		
	}
	.content{
		padding:30rpx;
		padding-top:30rpx;
		.row{
			padding:20rpx 0;
			border-bottom:1rpx #e2e2e2 dotted;
		}
	}
	.nohistory{
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
		image{
			width: 500rpx;
		}
		.text{
			font-size: 30rpx;
			color:#888;
		}
	}
}
</style>
