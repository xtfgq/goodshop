<template>
	
 <view class="swiper" style="padding-top: 0upx;background: white" v-if="list.length>0">
 				<swiper class="swiper-container" :autoplay="true" :interval="4000" :circular="true" :indicator-dots="true"
 				 indicator-active-color="#e10a07" indicator-color="#cccccc" style="height: 480upx;padding: 18upx 16upx 8upx 16upx">
 					<block v-for="(item, index) in list" :key="index">
 						<swiper-item class="swiper-wrapper">
 							<image  :src="item.url" style="width: 100%;height: 460upx" mode="scaleToFill"></image>
 						</swiper-item>
 					</block>
 				</swiper>
 			</view>
</template>

<script>
	export default {
		data() {
			return {
					
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
