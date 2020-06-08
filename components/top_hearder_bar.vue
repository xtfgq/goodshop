<template>
	
	<view class="cu-custom" :style="[{height:CustomBar + 'px'}]">
		<view class="cu-bar bg-white text-black bg-img" :style="style" >
			<view class="action " @tap="BackPage" v-if="isHeaderBack">
				<text class="cuIcon-back"></text>
			</view>
			<view class="content" :style="[{top:StatusBar + 'px'}]">
				<slot name="content">{{hearderTitle}}</slot>
			</view>
			<slot name="right">
				<image src="/static/img/home/share.png" class="image_right" @click="clickMe"></image>
			</slot>
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
	computed: {
		style() {
			var StatusBar= this.StatusBar;
			var CustomBar= this.CustomBar;
			var style = `height:${CustomBar}px;padding-top:${StatusBar}px;`;
			
			return style
		}
	},
	methods: {
		BackPage() {
			uni.navigateBack({
				delta: 1
			});
		},
		clickMe(){
			this.$emit("right")
		}

	},
		props:{
			hearderTitle: { 
				type: String,
				required: true
			},
			isHeaderBack: {
				type: Boolean,
				required: true
			},
		}
	}
</script>

<style>
	.image_right{
		width: 48rpx;
		height: 48rpx;
		margin-right: 12rpx;
	}
	
</style>
