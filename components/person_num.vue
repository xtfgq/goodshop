<template>
	
  <view class="flex-sub  ">
		<view class="grid  col-4 no-border margin-lr-lg" >
			<view  v-for="(item,index) in list" :key="index">
				<view v-if="item.image!=''"class="cu-avatar  radius margin-tb-xs":style="[{ backgroundImage:'url(' + item.image + ')' }]"></view>
				<view v-else="item.image==''"class="cu-avatar radius margin-tb-xs bg-gray">{{list.length-1}}</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
					StatusBar: this.StatusBar,
					CustomBar: this.CustomBar,
			};
		},

		props:{
				list: { 
					type: Array,
					required: true
				}
				
			}

		
	}
</script>

<style>

	
</style>
