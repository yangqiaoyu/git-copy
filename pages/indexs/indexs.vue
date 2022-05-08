<template>
	<view class="main_content">
		<view class="header">
			<text class="header_left">
				<text class="iconImg">
					<image src="/static/indexImg/xiaoxi2.png">
				</text>
				<text class="newsNotice">有新的消息提醒!</text>
			</text>
			<text class="header_right">
				<image src="/static/indexImg/X.png">
			</text>
		</view>
		<view class="exam">
			<view class="exam_left">
				<text class="inner">
					<image src="/static/indexImg/shijian.png">
				</text>
				<text class="inner">考试倒计时：<text></text>313天</text>
				<text class="inner">
					<image src="/static/indexImg/shezhi.png">
				</text>
			</view>
			<view class="exam_right">
				<checkbox-group>
					<label>
						检验师<checkbox value="cb" checked="true"  style="transform:scale(0.7)" />
					</label>
				</checkbox-group>
			</view>
		</view>
		<view class="swiperScroll">
			
		</view>
	</view>
</template>
<script>
	export default {
		data() {
			return {

			}
		},
		methods: {

		}
	}
</script>

<style style="scoped">
	.main_content {
		width: 100%;
		// background: #ccc;
		height: 100%;
	}

	.header {
		width: 100%;
		padding: 0 30rpx;
		color: #fff;
		height: 80rpx;
		background: #ff4081;
		line-height: 80rpx;
		display: flex;
		/* font-size: 24rpx; */
	}

	.header_left {
		flex: 2;
	}

	.iconImg {
		/* vertical-align: middle; */
	}

	.iconImg image {
		width: 28rpx;
		height: 32rpx;
		vertical-align: middle;
	}

	.newsNotice {
		padding-left: 10px;
		font-size: 24rpx;
	}

	.header_right {
		flex: 1;
	}

	.header_right image {
		width: 24rpx;
		height: 24rpx;
		padding-left: 60%;
		vertical-align: middle;
	}

	.exam {
		width: 100%;
		height: 72rpx;
		line-height: 72rpx;
		margin-top: 20rpx;
		margin-bottom: 30rpx;
		display: flex;
	}

	.exam_left {
		width: 50%;
		height: 100%;
		color: #666666;
		background: #F2F2F2;
		display: flex;
		font-size: 14rpx;
		border-radius:0rpx 10rpx 10rpx 0rpx;
	}

	.exam_left .inner:nth-child(1) {
		flex: 1;
		text-align: center;
	}

	.exam_left .inner:nth-child(2) {
		flex: 3;
		text-align: center;
		font-size: 26rpx;
	}

	.exam_left .inner:nth-child(3) {
		flex: 1;
		text-align: center;
	}

	.exam_left .inner image {
		width: 24rpx;
		height: 24rpx;
		vertical-align: middle;
	}

	.exam_right {
		width: 25%;
		color:#666666;
		height: 100%;
		background: #F2F2F2;
		display: flex;
		border-radius:10px 0px 0px 10px;
		margin-left: 25%;
		font-size:26rpx;
	}
	.exam_right uni-checkbox-group{
		    width: 100%;
		    text-align: center;
	}
	.swiperScroll{
		background:rgba(249,249,249,1);
	}
</style>
