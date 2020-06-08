<template>
	<view style="margin-bottom: 180rpx;" >

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
		<view class="bg-white">

		<view class="cu-list grid margin-lr col-4 no-border" style="padding-top: 10px;padding-bottom: 10px;">
			<view  v-for="(nav,index) in navlist" :key="index" >
				<view class="has-pdtb-4">
					<image :src="nav.image" mode="widthFix" style="height: 45px;width: 45px"></image>

					<view style="margin-top: 2px" class="is-size-14">{{nav['title']}}</view>
				</view>
			</view>
		</view>

		<view class="cu-list grid margin-lr col-2 no-border bg-white">
				<view  v-for="(item,index) in navmenu" :key="index" class="bg-white" @tap="goChild(item.title)">
					<view class="flex flex-wrap">
						<view class="basis-lg">
							<view style="margin-top: 14px;margin-left: 12px;font-size: 14px;font-weight: bold;">
								{{item.title}}
							</view>
							<view style="margin:7px;color: #414141;font-size: 12px;font-weight: bold;">
								<text class="text-price">{{item.price}}</text>
							</view>
							<view style="color:rgba(127,134,153,1);font-size: 12px;margin-left: 8px">{{item.num}}人付款</view>
							<view style="border-radius: 5px;margin-left: 7px;margin-right: 7px" class="bg-red">
								<text class="text-white text-sm">3日内成交有效</text>
							</view>
						</view>

					<image :src="item.image"  class="basis-xs item_image margin-left-lg"></image>
				</view>
			</view>
		</view>
		</view>
		<view class="bg-gray">
			<view class="cu-list grid  col-2 border bg-white ">
				<view  v-for="(item,index) in list" :key="index" class=" itemScreen" @tap="goChild(item.name)">
					<view class="item_border bg-white">
					<view class="cu-bar  bg-white">
						<view class="action">
							<text class="text-price text-black text-df">{{item.price}}</text>
						</view>
						<view class="action">
							<text class="text-gray text-sm">{{item.num}}人付款</text>

						</view>
					</view>
					<view class="cu-bar  bg-white margin_item">
						<view style="border-radius: 5px;margin-left: 7px;margin-right: 7px" class="bg-red">
							<text class="text-white text-sm padding-lr-sm ">3日内成交有效</text>
						</view>

					</view>
					<image :src="item.image"  style="width: 100%;height: 300rpx" mode="scaleToFill" class="bg-white"></image>
					<view class=" bg-white margin-left-xs item_border_text grid text-left">
						<span class="text-sm" style="display: -webkit-box;-webkit-box-orient: vertical;-webkit-line-clamp: 2;overflow: hidden;">{{item.name}}</span>
						<image src="/static/img/home/code.png"  class="tips_code"></image>
					</view>
					</view>
				</view>
			</view>
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

		border:12rpx solid #f2f2f2;

	}



	.is-size-14 {
		font-family: "Franklin Gothic Medium";
		font-size: 28 rpx !important;
		color: #333333;
	}
	.item_border{
		border-radius: 65rpx;
	}
	.item_image{
		margin-top: 40rpx;
	    height: 100rpx;
		width:100rpx;

	}
	.margin_item{
		margin-top: -35rpx;
	}
	item_image_list{
		height: 60rpx;
		width:60rpx;
	}
	.has-pdtb-4 {
		padding-top: 8 rpx !important;
		padding-bottom: 8 rpx !important;
	}
	.item_border_text{
		border:2rpx solid #EEEFF3;
		flex-direction: column;
	}
	.tips_code{
		width: 290rpx;
		height: 78rpx;
	}
</style>
