<template>
    <van-tabbar v-model="active" active-color="#1baeae" route="true">
        <van-tabbar-item to="/home" icon="home-o">首页</van-tabbar-item>
        <van-tabbar-item to="/category" icon="bar-chart-o">分类</van-tabbar-item>
        <van-tabbar-item to="/cart" icon="cart-o" :badge="badgeNum ? badgeNum : ''">购物车</van-tabbar-item>
        <van-tabbar-item to="/user" icon="friends-o">我的</van-tabbar-item>
    </van-tabbar>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue';
import { useStore } from 'vuex';
const active = ref(0);
const store = useStore();

const badgeNum = computed(() => {
    return store.state.cartCount
});

onMounted(() => {
    store.dispatch('setCartCouuntAction') // store 中 actions 里面的函数调用都用用dispatc调用
})

</script>

<style lang="less" scoped></style>