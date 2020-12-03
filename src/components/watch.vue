<template>
    <div>
        <h1>watch</h1>
        <p>{{ count }}</p>
        <button @click="change">改变</button>
    </div>
</template>

<script>
    import { watch, ref, watchEffect } from 'vue';
    export default {
        name: "watch",
        setup() {
            const count = ref(0);
            watch(() => count.value, (value, oldValue) => {
                console.log('new value', value);
                console.log('old value', oldValue);
            });
            watchEffect(() => {
                // 不需要手动传入依赖
                // 每次初始化时会执行一次回调函数来自动获取依赖
                // 无法获取到原值，只能得到变化后的值
                console.log('watchEffect>>>', count.value);
            });
            const change = () => {
                count.value++;
            }
            return {
                count,
                change,
            }
        }
    }
</script>

<style scoped>

</style>