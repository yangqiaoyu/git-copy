<template>
	<view>
		<view class="banner-info">
			<view class="grade-image">
				<image src="/static/vip/Grade.png"></image>
			</view>
			<view class="custService">
				<image src="/static/vip/custService.png"></image>
				<text class="custSer-info">联系客服</text>
			</view>
			<view class="integral">
				<view class="text">普通积分: 200</view>
				<view class="text">现金积分: 200</view>
			</view>
			<view class="stpe-top">
				<uni-steps :options="[{title: '未激活用户'}, {title: '激活用户'}, {title: '铜牌会员'}, {title: '银牌会员'}, {title: '金牌会员'}]" :active="3" active-color="#EFCF48"></uni-steps>
			</view>
		</view>
		<!-- 金牌会员特权 -->
		<view class="goldMedVIP">
			<view class="goleHeade">
				<view>
					<image src="/static/vip/goldMedal.png" class="goldImg"></image>
					<text class="goldTitle">金牌员特权</text>
				</view>
				<view class="openbtn">开通</view>
			</view>
			<view class="gole-info">您将拥有最高特权，【医学检验技术师(初级)】专业组的所有试题、试卷、真题等 均免费使用，软件的所有功能将会全部开放。详细特权如下：</view>
			<view class="example-body">
				<uni-grid :column="4" :highlight="true" :show-border="false">
					<uni-grid-item v-for="(item, index) in list" :key="index">
						<image :src="item.url" class="image"  />
						<text class="text">{{ item.text }}</text>
					</uni-grid-item>
				</uni-grid>
			</view>
		</view>
		<!-- 下一级特权 -->
		<view class="goldMedVIP">
			<view class="goleHeade">
				<view>
					<text class="goldTitle">下一级特权</text>
				</view>
				<view class="openbtn">开通</view>
			</view>
			<view class="example-body">
				<uni-grid :column="4" :highlight="true" :show-border="false">
					<uni-grid-item v-for="(item, index) in list" :key="index">
						<image :src="item.url" class="image"  />
						<text class="text">{{ item.text }}</text>
					</uni-grid-item>
				</uni-grid>
			</view>
		</view>
		<!-- 底部按钮 -->
		<view class="vipfooter">
			<view @click="togglePopup( 'expen')">免费体验7天</view>
			<view class="actives" @click="togglePopup('vip')">购买会员</view>
		</view>
		<!-- 七天试用 -->
		<uni-popup  type="center"   ref="expen">
			<view class="openExpen">
				<image class="image" align="center" src="/static/vip/show.png" mode="scaleToFill" />
				<view class="text">免费体验七天</view>
				<view class="text open-font-size">您将免费体验到黄金会员的所有权限(除有尝资料下载)</view>
				<view class="openbtn">立即开通</view>
			</view>
		</uni-popup>	
		<!-- 开通会员 -->
		<uni-popup type="center"   ref="vip">
			<view class="openExpen">
				<view class="text">开通会员</view>
				<view class="tui-row">
					<view class="tui-col tui-col-2">
					  <view class="gallery-box">
					    <text class="gallery-text gallery-time">一年</text>
						<text class="gallery-text gallery-money">¥68.00</text>
						<text class="gallery-text text-line">¥68.00</text>
						<text class="gallery-vip">金牌会员</text>
					  </view>
					</view>
					<view class="tui-col tui-col-2">
					  <view class="gallery-box">
					    <text class="gallery-text gallery-time">一年</text>
						<text class="gallery-text gallery-money">¥68.00</text>
						<text class="gallery-text text-line">¥68.00</text>
						<text class="gallery-vip">金牌会员</text>
					  </view>
					</view>
					<view class="tui-col tui-col-2">
					  <view class="gallery-box">
					    <text class="gallery-text gallery-time">一年</text>
						<text class="gallery-text gallery-money">¥68.00</text>
						<text class="gallery-text text-line">¥68.00</text>
						<text class="gallery-vip">金牌会员</text>
					  </view>
					</view>
				</view>
			</view>
		</uni-popup>	
	</view>
</template>

<script>
	import uniSteps from '@/components/uni-steps/uni-steps.vue'
	import uniGrid from "@/components/uni-grid/uni-grid.vue"
	import uniGridItem from "@/components/uni-grid-item/uni-grid-item.vue"
	import uniPopup from "@/components/uni-popup/uni-popup.vue"
	export default {
		data() {
			return {
				showexpen: false,
				showvip: false,
				content:'',
				type:'',
				list: [{
						url: '/static/indexImg/shoucang2.png',
						text: '免费题库'
					},
					{
						url: '/static/indexImg/shoucang2.png',
						text: '免费题库'
					},
					{
						url: '/static/c2.png',
						text: '免费题库'
					},
					{
						url: '/static/c3.png',
						text: '免费题库'
					},
					{
						url: '/static/indexImg/shoucang2.png',
						text: '免费题库'
					}]
			};
		},
		components: {
			uniSteps,
			uniGrid,
			uniGridItem,
			uniPopup
		},
		methods:{
			togglePopup(type) {
				switch (type) {
					case 'expen':
						this.content = '免费体验7天'
						this.$refs.expen.open()
						break		
					case 'vip':
						this.content = '开通会员'
						this.$refs.vip.open()
						break
				}
			},
		}
	}
</script>

<style lang="scss">
	page {
		background-color: #f9f9f9;
	}
	.banner-info{
		width: 100%;
		height: 447rpx;
		background:#3C4759;
		padding-top: 50rpx;
		.grade-image{
			width: 242rpx;
			height: 195rpx;
			margin: 0 auto;
		}
		.grade-image image{
			width: 100%;
			height: 100%;
		}
		.custService{
			.custSer-info{
				position: absolute;
				top: 60rpx;
				right: 12rpx;
				display: block;
				color: #fff;
				font-size: 20rpx;
			}
		}
		.custService image{
			position: absolute;
			top: 16rpx;
			right: 36rpx;
			width: 36rpx;
			height: 36rpx;
		}
		.integral{
			display: flex;
			-webkit-justify-content: center;
			justify-content: center;
			.text {
				margin: 15rpx 10rpx;
				padding: 0 20rpx;
				height: 70rpx;
				line-height: 70rpx;
				text-align: center;
				color: #fff;
				font-size: 30rpx;
			}
		}
		.stpe-top{
			margin: 38rpx;
		}
	}
	.goldMedVIP{
		margin-top: 40rpx;
		background: #fff;
		padding: 22rpx 22rpx 0 22px;
		.goleHeade{
			display: flex;
			justify-content: space-between;
			align-items: center
		}
		 .goldTitle{
			 font-size: 30rpx;
		 }
		 .openbtn{
			 font-size: 18rpx;
			 background:linear-gradient(159deg,rgba(255,204,0,1),rgba(255,138,0,1));
			 border-radius:16rpx;
			 color: #3C4759;
			 height: 30rpx;
			 line-height: 30rpx;
			 padding: 8rpx 28rpx 4rpx 28rpx;
		 }
		.example-body {
			flex-direction: row;
			flex-wrap: wrap;
			justify-content: center;
			padding: 5rpx;
			margin-top: 20rpx;
			font-size: 14rpx;
			background-color: #ffffff;
			display: block; 
			border-top: 1rpx solid #e5e5e5;
			.uni-grid-item{
				border-bottom: 1rpx solid #e5e5e5;
			}
			.text{
				font-size: 24rex;
				color: #333;
				text-align: center;
				margin-bottom: 10rpx;
				
			}
		}
		 .example-body .image{
			 width: 50rpx;
			 height: 50rpx;
			 margin: 26rpx auto;
		 }
		 .gole-info{
			 margin-top: 6rpx;
			 color: #7a7a7a;
			 font-size: 18rpx;
		 }
	}
	.goldImg{
		width: 32rpx;
		height: 43rpx;
		vertical-align: middle;
	}
	.vipfooter{
		position: fixed;
		bottom: 0;
		display: flex;
		background: #fff;
		height: 98rpx;
		line-height: 98rpx;
		right: 0;
		left: 0;
		text-align: center;
		box-shadow: -2rpx -2rpx 6rpx #f5f5f5;
		font-size: 30rpx;
		color: #27AE60;
		view{
			width: 50%;
		}
		.actives{
			background: #27AE60;
			color: #fff;
		}
	}
	.openExpen{
		background:linear-gradient(159deg,rgba(255,204,0,1),rgba(255,138,0,1));
		border-radius:20px;
		padding: 0rpx 40rpx 2rpx 40rpx;
		.image{
			display: block;
			width:209rpx ;
			height: 211rpx;
			margin: 0rpx auto;
			padding: 70rpx 0rpx;
		}
		.text{
			font-size:36rpx;
			font-weight:300;
			text-align: center;
		}
		.open-font-size{
			font-size: 18rpx;
			margin: 24rpx 0rpx;
		}
		.openbtn{
			background:linear-gradient(159deg,rgba(255,0,216,1),rgba(174,0,255,1));
			border-radius:16rpx;
			font-size: 24rpx;
			text-align: center;
			width:275rpx;
			height:47rpx;
			line-height: 47rpx;
			color: #fff;
			margin: 79rpx auto;
			
		}
	}
	.tui-row{
	  padding: 5px;
	  display: -webkit-flex;
	  display: flex;
	  align-items: center;
	  justify-content: space-between;
	  flex-wrap: wrap;
	}
	.tui-col-2 {
	  width:30%;
	  flex: 0 0 auto;
	  background:#fff;
	  border:2rpx solid #37006F;
	  border-radius:5px;
	}
	
	.gallery-box{
	  padding: 5rpx;
	  .text-line{
		  text-decoration:line-through;
		  font-size: 16rpx;
		  color: #6a6a6a;
	  }
	  .gallery-time{
		  font-size: 20rpx;
	  }
	  .gallery-money{
		font-size: 30rpx; 
		color: #37006F;
		line-height: 80rpx;
	  }
	  .gallery-vip{
		  display: block;
		  background: #fc0;
		  font-size: 16rpx;
		  text-align: center;
		  border-radius: 15rpx;
		  width: 50%;
		  margin: 0 auto;
		  
	  }
	}
	.gallery-text{
	  display: block;
	  text-align: center;
	  height: 60rpx;
	  line-height: 60rpx;
	  overflow: hidden;
	  white-space: nowrap;
	  text-overflow: ellipsis;
	}
</style>
