<template>
	<view class="dt-list-item" :class="isLast ? 'last':''">
		<view class="dt-list-contents" :class="!isLast ? 'has-border':''">
			<view class="title">
				{{info.title}}
			</view>
			<view class="num item">{{info.num}}/{{info.total}}</view>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			isLast:{
				type: Boolean,
				default: false
			},
			info:{
				type: Object,
				default: () => {
					return {}
				}
			}
		},
		data() {
			return {
				
			};
		}
	}
</script>

<style  lang="scss" scoped>
.dt-list-item {
	width:100%;
	overflow: hidden;
	position: relative;
    &:after {
		content:'';
		display:block ;
		width:1px;
		height:80px;
		background:#27AE60;
		top: 0;
		left: 17px;
		position: absolute;
	}
	&:before {
		content:'';
		display:block ;
	    width: 7px;
		height:7px;
		background:#27AE60;
		border-radius: 4px;
		position: absolute;
		left: 14px;
		top: 21px;
	}
	&.last {
		&:after {
			content:'';
			display:block ;
			width:1px;
			height:26px;
			background:#27AE60;
			top: 0;
			left: 17px;
			position: absolute;
		}
	}
	.dt-list-contents {
		padding: 14px 12px 14px 34px;
		justify-content: flex-start;
		position: relative;
		&.has-border{
			
			&:after {
				content:'';
				display:block ;
				width:calc(100vw - 34px);
				height:1px;
				background:#ddd;
				bottom:0;
				right:0;
				position: absolute;
			}
		}
	}
	.title {
		font-size:15px;
		font-weight:400;
		color:rgba(51,51,51,1);
	}
	.num {
		 font-size:14px;
		 font-weight:400;
		 color:#999;
		 position:relative;
		 padding-top:4px;
	}
	
}
</style>
