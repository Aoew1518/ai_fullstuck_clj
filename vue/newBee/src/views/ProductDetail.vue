<template>
    <div>
        <SimpleHeader :title="'商品详情'" />

        <div class="detail-content">

            <div class="detail-swipe-wrap">
                <van-swipe class="my-swipe" indicator-color="#1baeae">
                    <van-swipe-item v-for="(item, index) in state.detail.goodsCarouselList" :key="index">
                        <img :src="item" alt="">
                    </van-swipe-item>
                </van-swipe>
            </div>

            <div class="product-info">
                <div class="product-title">{{ state.detail.goodsName }}</div>
                <div class="product-desc">免邮费 顺丰快递</div>
                <div class="product-price">￥{{ state.detail.sellingPrice }}</div>
            </div>

            <div class="product-intro">
                <ul>
                    <li>概述</li>
                    <li>参数</li>
                    <li>安装服务</li>
                    <li>常见问题</li>
                </ul>
            </div>

            <div class="product-content" v-html="state.detail.goodsDetailContent"></div>

        </div>

        <FooterBar :id="route.query.id"/>
    </div>
</template>

<script setup>
import SimpleHeader from '@/components/SimpleHeader.vue';
import { useRoute, useRouter } from 'vue-router'; // 是路由的描述
import { onMounted, reactive} from 'vue';
import { getDetail } from '../api/goods.js'
import FooterBar from '@/components/FooterBar.vue';

const route = useRoute();   // 当前页面url的详细描述route
const router = useRouter(); // 路由的实例对象router
const state = reactive({
  detail: {}
})

console.log(route);

onMounted(async () => {
    // 从url取到id值，将商品的id传给后端， 获取该商品的详细信息
    const { id } = route.query;
    // const{ query:{ id } } = route
    // 调用接口，获取商品的详细信息
    const { data } = await getDetail(id);
    console.log(data); // 接口请求代码都要注意异步
    state.detail = data;
})
</script>

<style lang="less" scoped>
.detail-content {
    height: calc(100vh - 44px);
    overflow: scroll; // 超出滚动

    .detail-swipe-wrap {
        .my-swipe {
            img {
                width: 100%;
            }
        }
    }

    .product-info {
        padding: 0 10px;

        .product-title {
            font-size: 18px;
            color: #333;
        }

        .product-desc {
            font-size: 14px;
            color: #999;
            padding: 10px 0;
        }

        .product-price {
            color: #f63515;
            font-size: 22px;
        }
    }

    .product-intro {
        width: 100%;
        padding-bottom: 50px;
        overflow: auto;

        ul {
            display: flex;
            margin: 10px;

            li {
                flex: 1; // 等比例放大1，类似于都是1：1：1：1等比例
                font-size: 15px;
                padding: 5px 0;
                text-align: center;
                border-right: 1px solid #999;

                &:last-child {
                    border-right: none;
                }
            }
        }
    }

    .product-content {
        padding: 0 20px;

        img {
            width: 100%;
        }
    }
}
</style>