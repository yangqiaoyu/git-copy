<template>
	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
		<view class="www">
			bbbbbbbbbbbbbbbbbbbbbb
		</view>
		<!-- 有圈圈 手风琴效果 --> 
		<uni-collapse accordion="true">
		    <dt-collapse-item  v-for="(item,index) in list" :key="index" :info="item">
		        <dt-list-item v-for="(items,idx) in item.children" :key="idx" :info="items" :isLast="idx === item.children.length-1">
					
				</dt-list-item>
		    </dt-collapse-item>
		  <!--  <dt-collapse-item title="标题文字">
		        <dt-list-item>
		        	
		        </dt-list-item>
		    </dt-collapse-item>
		    <dt-collapse-item title="标题文字">
		       <dt-list-item>
		      	
		       </dt-list-item>
		    </dt-collapse-item> -->
		</uni-collapse>
	</view>
</template>

<script>
	import uniCollapse from '@/components/uni-collapse/uni-collapse.vue'
	import dtCollapseItem from '@/components/dt-collapse-item.vue'
	import dtListItem from '@/components/dt-list-item.vue'
	export default {
		data() {
			return {
				title: 'Hello',
				list:[
					{ 
						title:'第一章、血液样本采集和血涂片制备',
					    num:'0', 
						total:'22',
						children:
						[
							{title:'第一章、血液样本采集和血涂片制备(-)',num:'0',total:'22'},
							{title:'血液样本采集和血涂片制备123',num:'1',total:'27'},
						]
				    },
					{
						title:'第二章、红细胞检查',
					    num:'0', 
						total:'22',
						children:
						[
							{title:'红细胞检查（一）',num:'0',total:'22'},
							{title:'红细胞检查（二）',num:'1',total:'27'},
							{title:'红细胞检查（三）',num:'33',total:'17'},
						]
					},
			    ]
			}
		},
		components: {
			uniCollapse,
			dtCollapseItem,
			dtListItem
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>
	/* .content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.www {
		width:300rpx;
		height:100rpx;
		background: red;
	} */

</style>
