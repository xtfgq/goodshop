<template>
	<view style="margin-bottom: 150upx;" >
		<view class="swiper" style="padding-top: 0upx;background: white" v-if="swiperList.length>0">
			<swiper class="swiper-container" :autoplay="true" :interval="4000" :circular="true" :indicator-dots="true"
			 indicator-active-color="#e10a07" indicator-color="#cccccc" style="height: 480upx;padding: 18upx 16upx 8upx 16upx">
				<block v-for="(item, index) in swiperList" :key="index">
					<swiper-item class="swiper-wrapper">
						<image  :src="item.url" style="width: 100%;height: 460upx" mode="scaleToFill"></image>
					</swiper-item>
				</block>
			</swiper>
		</view>




	</view>

	


</template>

<script>
	export default {
		name: "swiperContent",
		props: {
			
		},
		
		data() {
			return {

			
				swiperList: [{
								id: 0,
								type: 'image',
								url: 'http://linjiashop-mobile-api.microapp.store/file/getImgStream?idFile=00950b78-0fc6-4e88-b663-07dc46a2b6df.jpg'
							}, {
								id: 1,
								type: 'image',
								url: 'http://linjiashop-mobile-api.microapp.store/file/getImgStream?idFile=8974ee52-c261-440a-84d3-8f8c1bd43a6a.jpg',
							}, {
								id: 2,
								type: 'image',
								url: 'http://linjiashop-mobile-api.microapp.store/file/getImgStream?idFile=2ba1e87f-f04e-40b5-8d99-63e035a9d752.jpg'
							}, {
								id: 3,
								type: 'image',
								url: 'http://linjiashop-mobile-api.microapp.store/file/getImgStream?idFile=8974ee52-c261-440a-84d3-8f8c1bd43a6a.jpg'
							}],
				navlist: [{
					
					title: "工艺品",
					image: "/static/img/home/tianmaojingxuan.png",
					url: '9'

				     },

					{
						title: "数码",
						image: "/static/img/home/gaoyongjingxuan.png",
						url: '1'

					},
					{
						title: "服饰",
						image: "/static/img/home/chaozhidapai.png",
						url: '8'

					},
					{
						title: "茶叶",
						image: "/static/img/home/juhuasuan.png",
						url: '4'

					},
					{

						title: "保健品",
						image: "/static/img/home/tianmaojingxuan.png",
						url: '9'

					},

					{
						title: "旅游",
						image: "/static/img/home/gaoyongjingxuan.png",
						url: '1'

					},
					{
						title: "珠宝首饰",
						image: "/static/img/home/chaozhidapai.png",
						url: '8'

					},
					{
						title: "更多",
						image: "/static/img/home/juhuasuan.png",
						url: '4'

					}
				],
				navmenu: [{

					title: "热门好物",
					image: "/static/img/home/tupian1.png",
					price: '2980.00',
					num:'205'

				},

					{
						title: "预售日历",
						image: "/static/img/home/tupian2.png",
						price: '2905.00',
						num:'214'

					},
					{
						title: "高价回购",
						image: "/static/img/home/tupian3.png",
						num:'2504',
						price: '2925.00',

					},
					{
						title: "最新降价",
						image: "/static/img/home/tupian4.png",
						num:'4',
						price: '2925.00',

					}

				],
				list: [{

					name: "2020年新春大礼包",
					image: "http://linjiashop-mobile-api.microapp.store/file/getImgStream?idFile=d6bb51c1-856e-4134-abbc-a59c4ce46603.jpg",
					price: '2980.00',
					num:'205'

				},

					{
						name: "热卖大红袍",
						image: "http://linjiashop-mobile-api.microapp.store/file/getImgStream?idFile=ea110379-87ec-42b2-aeaf-5e27410902f5.jpg",
						price: '2905.00',
						num:'214'

					},
					{
						name: "小茶灌礼盒",
						image: "http://linjiashop-mobile-api.microapp.store/file/getImgStream?idFile=b45f336e-983a-4ebf-aa3a-528e6aa2f390.jpg",
						num:'2504',
						price: '2925.00',

					},
					{
						name: "小茶灌礼盒套装小茶灌礼盒套装小茶灌礼盒套装小茶灌礼盒套装小茶灌礼盒套装小茶灌礼盒套装小茶灌礼盒套装小茶灌礼盒套装小茶灌礼盒套装",
						image: "http://linjiashop-mobile-api.microapp.store/file/getImgStream?idFile=d2c3b8a4-1ece-4f1f-a222-9f9e0ee11b15.jpg",
						num:'4',
						price: '2925.00',

					}

				]

			
			};
		},
		
		methods:{
			willShowPage(param){
				console.log( "第" + param + "页面展示")
			},
			/* 刷新 */
			refreashData(param){
				let msg = "你刷新的是第" + param + "页"
				uni.showToast({
					title:msg
				})
				
				setTimeout(()=>{
					this.$emit("onEndRefreash")
				}, 2000)
			},
			goChild(val){
				uni.navigateTo({
					url:'./goodsdetails'+'?title='+val
				})
			}
		}
	}
</script>

<style>


	.itemScreen{

		border:12upx solid #f2f2f2;

	}



	.is-size-14 {
		font-family: "Franklin Gothic Medium";
		font-size: 28 rpx !important;
		color: #333333;
	}
	.item_border{
		border-radius: 65upx;
	}
	.item_image{
		margin-top: 40upx;
	    height: 100upx;
		width:100upx;

	}
	.margin_item{
		margin-top: -35upx;
	}
	item_image_list{
		height: 30px;
		width:30px;
	}
	.has-pdtb-4 {
		padding-top: 8 rpx !important;
		padding-bottom: 8 rpx !important;
	}
	.item_border_text{
		border:2upx solid #EEEFF3;
		flex-direction: column;
	}
	.tips_code{
		width: 96upx;
		height: 96upx;
	}
</style>

