<template>
    <scroll-view class="bg-white " >
        <view style="margin-bottom: 128rpx">
            <swiper-list :list="swiperList"></swiper-list>
            <view style="text-align: center; width: 100%; ">
                <view  style="margin: 0 auto;">
                    <text class="text-black text-bold text-lg">最新价：</text>
                    <text class="text-price text-red text-lg">500</text>
                    <text class="text-red text-lg money_unit" >+3.53%</text>
                </view>
            </view>
            <scroll-view scroll-x class="bg-white nav text-center">
                <view class="cu-item" :class="index==TabCur?'text-black cur':''" v-for="(item,index) in topMenuDatas" :key="index" @tap="tabSelect" :data-id="index">
                    {{item.name}}
                </view>
            </scroll-view>
            <view class="cu-bar  bg-white " >
                <view class="action">
                    <text class="text-black text-bold">卖方报价</text>
                </view>
                <view class="action">
                    <text class="text-black text-bold">买方报价</text>
                </view>
            </view>
            <view class="flex">
                <view class="flex-sub  " >
                    <view v-for="(order,index) in sellItems" :key="index"
                          class="order_item bg-white grid col-4  text-lg  ">
                        <image :src="order.image"  class=" cu-avatar round  margin-top-sm"style="width:48rpx;height: 48rpx;margin-left: 12rpx">
                        </image>
                        <view class="text-black text-df text-center margin-top-sm" >
                           {{order.name}}</view>
                        <view class="text-center margin-tb-sm "><text class="text-price text-red">{{order.price}}</text></view>
                        <view class="text-black text-df  margin-tb-sm">{{order.num}}</view>
                    </view>
                </view>
                <view class="flex-sub" >
                    <view v-for="(order,index) in sellItems" :key="index"
                          class="order_item bg-white grid col-5  ">

                        <image :src="order.image"  class=" cu-avatar round  margin-top-sm"style="width:48rpx;height: 48rpx">
                        </image>
                        <view class="text-black text-df text-center  margin-top-sm" >
                           {{order.name}}
                        </view>
                        <view class="text-center margin-tb-sm "><text class="text-price text-red">{{order.price}}</text></view>
                        <view class="text-black text-df margin-tb-sm ">{{order.num}}</view>
                        <text class="cu-btn radius bg-yellow margin-tb-sm " >变现</text>
                    </view>
                </view>

            </view>

        </view>
        <view class="flex bg-white" style="position:fixed; bottom:0;height: 128rpx;width: 100%;">
            <view class="flex bg-yellow radius margin-tb-sm margin-lr-lg block " style="width: 95%;">
                <view class="flex-sub text-gray text-sm  " style="margin-top: 28rpx;margin-left: 15rpx" >没有合适的价格</view>
                <view class="flex-twice text-black text-lg" style="margin-top: 16rpx;margin-left: 64rpx">+卖出上架</view>
            </view>
        </view>
    </scroll-view>
</template>

<script>
    import SwiperList from "@/components/SwiperList.vue"
    import appShare, { closeShare } from "@/utils/share.js"
    export default {
        data() {
            return {
                TabCur: 0,
                scrollLeft: 0,
                title:'',
                topMenuDatas: [{
                    "id": 5,
                    "name": "寄售卖出"
                }, {
                    "id": 3,
                    "name": "专店卖出"
                }, {
                    "id": 1,
                    "name": "预售卖出"
                }, {
                    "id": 2,
                    "name": "促销卖出"
                }, {
                    "id": 10,
                    "name": "直播卖出"
                }],
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
                sellItems:[],
            };
        },
        // #ifndef MP


        //点击导航栏 buttons 时触发
        onNavigationBarButtonTap(e) {

            const index = e.index;
            if (index === 0) {
                this.onShare();
            }
        },
        // #endif
        components: {

            SwiperList

        },
        onLoad(options) {
            this.title = options.title;
            uni.setNavigationBarTitle({title: this.title});

        },
        onShow(){
            this.sellItems.length=0;
            for(let i=0;i<10;i++){
                let price = 38+i.toString();
                let img=i%2==0?"/static/img/home/boy.png":"/static/img/home/girl.png";
                let name=i%2==0?'郭**':'张**';
                let obj ={
                    price:price,
                    name:name,
                    num:280,
                    image:img
                }
                this.sellItems.push(obj);
            }
        },
        methods: {
            tabSelect(e) {
                this.TabCur = e.currentTarget.dataset.id;
                this.scrollLeft = (e.currentTarget.dataset.id - 1) * 60
            },

            onShare(){
                // #ifdef APP-PLUS
                let shareData = {
                    shareUrl:"https://kemean.com/",
                    shareTitle:"分享的标题",
                    shareContent:"分享的描述",
                    shareImg:"http://qn.kemean.cn//upload/202004/18/1587189024467w6xj18b1.jpg",
                    appId : "wxd0e0881530ee4444", // 默认不传type的时候，必须传appId和appPath才会显示小程序图标
                    appPath : "pages/home/home",
                    appWebUrl : "https://kemean.com/",
                };
                let shareObj = appShare(shareData,res => {

                    closeShare();
                });
                setTimeout(() => {
                    // 第二种关闭弹窗的方式
                    shareObj.close();
                },5000);
                // #endif
                // #ifndef APP-PLUS
                uni.showToast({
                    title: '只能在app端支持分享',
                    duration: 2000,
                    icon: 'none',
                })

                // #endif
            },
        }
    }

</script>

<style>

    .order_item{
        height: 96rpx;
        border-bottom: 1px solid;
        border-bottom-color:#ededed;
        margin-top: -12rpx;
        margin-bottom: 12rpx;

    }

    .cu-btn {
        position: relative;
        border: 0upx;
        display: inline-flex;
        align-items: center;
        justify-content: center;
        box-sizing: border-box;
        padding: 0 15rpx;
        font-size: 24rpx;
        height: 48rpx;
        line-height: 1;
        text-align: center;
        text-decoration: none;
        overflow: visible;
        margin-left: 0rpx;
        transform: translate(0upx, 0upx);
        margin-right: initial;
    }
</style>
