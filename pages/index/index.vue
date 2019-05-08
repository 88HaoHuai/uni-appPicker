<template>
	<view class="content">
		<!-- <view class="tab" :class="[{'active':index==tabIndex}]" @tap="toggleTab(index)" v-for="(item,index) in tabList" :key="index">{{item.name}}</view>
		<w-picker :mode="mode" startYear="2018" endYear="2030" step="1" :defaultVal="defaultVal" @confirm="onConfirm" ref="picker" themeColor="#f00"></w-picker> -->
		
		<view class="tab" @tap="toggleTab1(2)" :key="2">开始日期时间选择分钟</view>
		<view class="tab" @tap="toggleTab1(3)" :key="3">开始半日时间选择</view>	
		<w-picker :mode="mode" startYear="2019" endYear="2030" step="1" :defaultVal="defaultVal1" @confirm="onConfirm1" ref="picker1" themeColor="#f00"></w-picker>
		<view class="">{{startTime}}</view>
		
		<view class="tab" @tap="toggleTab2(2)" :key="2">结束日期时间选择分钟</view>
		<view class="tab" @tap="toggleTab2(3)" :key="3">结束半日时间选择</view>	
		<w-picker :mode="mode" startYear="2019" endYear="2030" step="1" :defaultVal="defaultVal2" @confirm="onConfirm2" ref="picker2" themeColor="#f00"></w-picker>
		<view class="">{{endTime}}</view>
		
	</view>
</template>

<script>
	import wPicker from "@/components/w-picker/w-picker.vue";
	export default {
		components:{
			wPicker
		},
		data() {
			return {
				startTime:'开始',
				endTime:'结束',
				title: 'Hello',
				// tabList:[{
				// 	mode:"date",
				// 	name:"日期选择",
				// 	value:[0,1,0]
				// },{
				// 	mode:"yearMonth",
				// 	name:"年月",
				// 	value:[0,1]
				// },{
				// 	mode:"dateTime",
				// 	name:"日期时间选择秒",
				// 	value:[1,1,1,1,2,5]
				// },{
				// 	mode:"dateTimeMinutes",
				// 	name:"日期时间选择分钟",
				// 	value:[1,1,1,1,2]
				// },{
				// 	mode:"dateTimeHalfDay",
				// 	name:"半日时间选择",
				// 	value:[1,1,1,0]
				// },{
				// 	mode:"time",
				// 	name:"时间选择",
				// 	value:[1,1,0]
				// },
				// {
				// 	mode:"region",
				// 	name:"省市区",
				// 	value:[10,0,5]
				// }],
				tabList:[{
					mode:"date",
					name:"年月日选择",
					value:[0,0,0]
				},{
					mode:"yearMonth",
					name:"年月选择",
					value:[0,0]
				},{
					mode:"dateTimeMinutes",
					name:"日期时间选择分钟",
					value:[0,0,0,0,0]
				},{
					mode:"dateTimeHalfDay",
					name:"半日时间选择",
					value:[0,0,0,0]
				}],
				tabIndex:0
			}
		},
		computed:{
			mode(){
				return this.tabList[this.tabIndex].mode
			},
			defaultVal1(){
				return this.tabList[this.tabIndex].value
			},
			defaultVal2(){
				return this.tabList[this.tabIndex].value
			}
		},
		onLoad() {

		},
		methods: {
			
			toggleTab1(index){
				this.tabIndex=index;
				this.$refs.picker1.show();
			},
			onConfirm1(val){
				console.log(JSON.stringify(val));
				// this.startTime = JSON.stringify(e['result']).toString().replace(/\"/g, "");
				this.startTime=JSON.stringify(val['result']).toString().replace(/\"/g, "");
			},
			toggleTab2(index){
				this.tabIndex=index;
				this.$refs.picker2.show();
			},
			onConfirm2(val){
				console.log(JSON.stringify(val));
				this.endTime=JSON.stringify(val['result']).toString().replace(/\"/g, "");
			}
		}
	}
</script>

<style>
	.content {
		text-align: center;
		height: 400upx;
	}
	.tab{
		padding:20upx 0;
		font-size: 32upx;
	}
	.tab.active{
		color:#f00;
	}
</style>
