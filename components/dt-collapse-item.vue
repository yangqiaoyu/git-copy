<template>
	<view :class="{ 'uni-collapse-cell--disabled': disabled,'uni-collapse-cell--notdisabled': !disabled, 'uni-collapse-cell--open': isOpen,'uni-collapse-cell--hide':!isOpen }"
	 class="uni-collapse-cell">
		<view class="uni-collapse-cell__title" :class="isOpen?'active':''" @click="onClick">
			<view class="dt-collapse-content">
				<view class="title item">
					<view class="round" :class="isOpen?'active':''"></view>
					<view>{{info.title}}</view>
					<!-- #ifdef MP-ALIPAY -->
					<view :class="{ 'uni-collapse-cell__title-arrow-active': isOpen, 'uni-collapse-cell--animation': showAnimation === true }"
					 class="uni-collapse-cell__title-arrow">
						<uni-icons color="#bbb" size="20" type="arrowdown" />
					</view>
					<!-- #endif -->
					<!-- #ifndef MP-ALIPAY -->
					<uni-icons :class="{ 'uni-collapse-cell__title-arrow-active': isOpen, 'uni-collapse-cell--animation': showAnimation === true }"
					 class="uni-collapse-cell__title-arrow" color="#bbb" size="20" type="arrowdown" />
					<!-- #endif -->
				</view>
				<view class="num item">{{info.num}}/{{info.total}}</view>
			</view>

		</view>
		<view :class="{'uni-collapse-cell__content--hide':!isOpen}" class="uni-collapse-cell__content">
			<view :class="{ 'uni-collapse-cell--animation': showAnimation === true }" class="uni-collapse-cell__wrapper" :style="{'transform':isOpen?'translateY(0)':'translateY(-50%)','-webkit-transform':isOpen?'translateY(0)':'translateY(-50%)'}">
				<slot />
			</view>
		</view>
	</view>
</template>

<script>
	import uniIcons from './uni-icons/uni-icons.vue'
	export default {
		name: 'UniCollapseItem',
		components: {
			uniIcons
		},
		props: {
			disabled: {
				// 是否禁用
				type: Boolean,
				default: false
			},
			showAnimation: {
				// 是否显示动画
				type: Boolean,
				default: true
			},
			open: {
				// 是否展开
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
				isOpen: false
			}
		},
		watch: {
			open(val) {
				this.isOpen = val
			}
		},
		inject: ['collapse'],
		created() {
			this.isOpen = this.open
			this.nameSync = this.name ? this.name : this.collapse.childrens.length
			this.collapse.childrens.push(this)
			if (String(this.collapse.accordion) === 'true') {
				if (this.isOpen) {
					let lastEl = this.collapse.childrens[this.collapse.childrens.length - 2]
					if (lastEl) {
						this.collapse.childrens[this.collapse.childrens.length - 2].isOpen = false
					}
				}
			}
		},
		methods: {
			onClick() {
				if (this.disabled) {
					return
				}
				if (String(this.collapse.accordion) === 'true') {
					this.collapse.childrens.forEach(vm => {
						if (vm === this) {
							return
						}
						vm.isOpen = false
					})
				}
				this.isOpen = !this.isOpen
				this.collapse.onChange && this.collapse.onChange()
				this.$forceUpdate()
			}
		}
	}
</script>

<style lang="scss" scoped>
	@import '@/uni.scss';

	.uni-collapse-cell {
		flex-direction: column;
		border-color: $uni-border-color;
		border-bottom-width: 1px;
		border-bottom-style: solid;
	}


	.uni-collapse-cell--hover {
		background-color: $uni-bg-color-hover;
	}

	.uni-collapse-cell--open {
		background-color: $uni-bg-color-hover;
	}

	.uni-collapse-cell--disabled {
		background-color: $uni-bg-color-hover;
		// opacity: 0.3;
	}


	// .uni-collapse-cell--hide {
	// 	height: 72px;
	// }

	.uni-collapse-cell--animation {
		// transition: transform 0.3s ease;
		transition-property: transform;
		transition-duration: 0.3s;
		transition-timing-function: ease;
	}

	.uni-collapse-cell__title {
		padding: 14px 12px;
		position: relative;
		/* #ifndef APP-NVUE */
		display: flex;
		width: 100%;
		box-sizing: border-box;
		/* #endif */
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		overflow: hidden;
		&.active {
		   background: #fff;
		   &:before {
			 content:'';
			 display: block;
			 width:100%;
			 height:1px;
			 position: absolute;
			 background: #eee;
			 left: 0px;
			 bottom:0px;
		   }
		   &:after {
			   content:'';
			   display: block;
			   width:1px;
			   height:50px;
			   position: absolute;
			   background: #27AE60;
			   left: 17px;
			    top: 30px;
			   
		   }
		}
	}

	.uni-collapse-cell__title:active {
		background-color: $uni-bg-color-hover;
	}


	.uni-collapse-cell__title-arrow {
		width: 20px;
		height: 20px;
		transform: rotate(0deg);
		transform-origin: center center;

	}

	.uni-collapse-cell__title-arrow-active {
		transform: rotate(180deg);
	}


	.uni-collapse-cell__content {
		overflow: hidden;
		background: #f9f9f9;
	}

	.uni-collapse-cell__wrapper {
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: column;
	}

	.uni-collapse-cell__content--hide {
		height: 0px;
		line-height: 0px;
	}
	.dt-collapse-content {
		width:100%;
		.item {
			padding-left:24px;
		}
		.title {
			 font-size:15px;
			 font-weight:400;
			 color:rgba(51,51,51,1);
			 display: flex;
			 flex-direction:row ;
			 justify-content: space-between;
			 position: relative;
		}
		.num {
			 font-size:14px;
			 font-weight:400;
			 color:#999;
			 position:relative;
			 padding-top:4px;
		}
		.round {
			position: absolute;
			width:12px;
			height:12px;
			border:1px solid #ddd;
			border-radius: 50%;
			left:-1px;
			top:50%;
			transform: translateY(-50%);
			&.active {
				border-color: #27AE60;
				&:after {
					content:'';
					display:block;
					width:8px;
					height:8px;
					position: absolute;
					top:50%;
					left:50%;
					transform: translate(-50%,-50%);
					background: #27AE60;
					border-radius: 50%;
				}
			}
		}

	}
</style>
