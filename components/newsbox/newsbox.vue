<template>
	<view class="newsbox">
		<view class="pic">
			<image :src="item.picurl" mode="aspectFill"></image>
		</view>
		<view class="text">
			<view class="title">{{item.title}}</view>
			<view class="info" v-if="!item.looktime">
				<text>{{item.author}}</text>
				<text>{{item.hits}}浏览</text>
			</view>
			<view class="info" v-else>
				<text>浏览时间：{{item.looktime}}</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"newsbox",
		props:{
			item:{
				type:Object,
				default(){
					return{
						title:"组件内标题",
						author:"zs",
						hits:699,
						picurl:"../../static/images/0.jpg",
					}
				}
			}
		},
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="scss" >
.newsbox{
	display: flex;
	justify-content: space-between;
	.pic{
		width: 230rpx;
		height: 160rpx;
		image{
			width: 100%;
			height: 100%;
		}
	}
	.text{
		flex:1;
		padding-left:20rpx;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		.title{
			.con{
				ftext-overflow: ellipsis;
				-webkit-line-clamp: 2;
				ont-size: 36rpx;
				color:#333;
				display: -webkit-box;
				overflow: hidden;
				-webkit-box-orient: vertical;
			}			
		}
		.info{
			font-size: 26rpx;
			color:#999;
			display: flex;
			.font{
				padding-right: 20rpx;
			}
		}
	}
}
</style>