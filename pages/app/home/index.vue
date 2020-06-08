<template>
	<scroll-view class="page bg-white ">
		<view class="cu-bar search margin-top-head ">
			<view class="search-form round">
				<text class="content cuIcon-search padding-tb-sm">
				</text>
				<input class="text-center" type="text" placeholder="新品上市" confirm-type="search"></input>

			</view>
		</view>
		<view>

			<view style=" background-color: #333333; color: black; width: 100%; ">
				<mh_segmentbar v-bind:curIndex=curMenuIndex :menuData="topMenuDatas" style="width: 100%;overflow: hidden;" ref="segmentbar"
				 @didSelectTopMenuItem="didSelectTopMenuItem" />
			</view>		

			<view style=" width: 100%; margin-top: 0rpx; height: 94%; position: absolute;">
				<swiper style=" width: 100%; position: absolute; overflow: scroll; height: 100% ;"
				 duration="300" :current="curMenuIndex" @change="changeSwipe" >
					
					<swiper-item v-for="(menuItem) in topMenuDatas" v-bind:key="menuItem.id" style="overflow: overlay; flex: 1; height: 100%;">
						
							<swiperContent ref="childView" @onStartRefreash="onStartRefreash" @onEndRefreash="onEndRefreash"> </swiperContent>
			
					
					</swiper-item>
				</swiper> 
			</view>
        </view>
		<view class="cu-tabbar-height"></view>
	</scroll-view>
</template>

<script>
	
	import mh_segmentbar from "@/components/mh-segmentbar/mh-segmentbar.vue"
	import swiperContent from "./swiperContent.vue"

	export default {
		data() {
			return {
				
				topMenuDatas: [{
					"id": 5,
					"name": "全部"
				}, {
					"id": 3,
					"name": "非遗"
				}, {
					"id": 1,
					"name": "家居"
				}, {
					"id": 2,
					"name": "期茶"
				}, {
					"id": 10,
					"name": "健康"
				}, {
					"id": 11,
					"name": "旅游"
				}, {
					"id": 12,
					"name": "传承"
				}],
				curMenuIndex: 0,
				navlist: [{
						title: "天猫精选",
						image: "../../static/img/home/tianmaojingxuan.png",
						url: '9'
				
					},
				
					{
						title: "今日上新",
						image: "../../static/img/home/gaoyongjingxuan.png",
						url: '1'
				
					},
					{
						title: "超值大牌",
						image: "../../static/img/home/chaozhidapai.png",
						url: '8'
				
					},
					{
						title: "聚划算",
						image: "../../static/img/home/juhuasuan.png",
						url: '4'
				
					}, {
						title: "热门分类",
						image: "../../static/img/home/gengduofenlie.png",
						url: 'remeng'
				
					}
				],
				
			}
		},
		components: {
					mh_segmentbar,
					swiperContent

		},
		/* 刷新  将刷新的页面索引传到content子页面中 在子页面进行请求*/
		onPullDownRefresh() {
			this.$refs.childView[this.curMenuIndex].refreashData(this.curMenuIndex) //传入页面 
			
		},
		
		methods: {
			/* 点击顶部菜单时 切换视图 */
			didSelectTopMenuItem(index) {
				if (this.curMenuIndex !== index) {
					this.curMenuIndex = index
				}
			},
		
		
			/* 手机滑动切换视图 */
			changeSwipe(event) {
				let cuIndex = event.detail.current
				this.$refs.segmentbar.didSelectItem(cuIndex) //改变顶部
		
				//在页面切换的时候停止刷新 
				this.onEndRefreash()
				this.$refs.childView[cuIndex].willShowPage(cuIndex) //如果不想在子页面请求数据， 在本页请求数据后再传入子页面也行  
			},
		
		
			/* 子页面主动请求刷新 */
			onStartRefreash() {
				uni.startPullDownRefresh()
			},
		
			/* 停止刷新 */
			onEndRefreash() {
				uni.stopPullDownRefresh()
			},
			scrollToppp(e) {
				//检测scrollView是否滑到顶部  在此可设置刷新开关 currentWebView设置
			}
		}
	}
</script>

<style scoped lang="scss">
	.page {
			height: 100vh;
	}


	.search-form{
		border-radius: 10rpx;
	}
	.margin-top-hearder {
		margin-top: 360rpx;
	}

	
	
	.nowrap {
		white-space: nowrap;
		overflow-x: scroll;
		height: 200rpx;
	}
	.margin-top-head {
		margin-top: 70rpx;
	}
	.item-t {
		display: inline-block;
		width: 100%;
		height: 200rpx;
	
		background: yellow;
	
		vertical-align: top;
	
	}

</style>
