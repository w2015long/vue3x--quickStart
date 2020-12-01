<template>
    <h1>toRaw</h1>
    <p>{{ state.age }}</p>
    <button @click="change">改变</button>
</template>
<script>
    import { toRaw, reactive } from 'vue';
    /*
    当我们想修改数据，但不想让视图更新时，可以选择直接修改原始数据上的值，
    因此需要先获取到原始数据，我们可以使用 Vue3 提供的 toRaw 方法
    **/
    export default {
        name: 'toRaw',
        props: {
            range: {
                type: Number,
                default: 10
            }
        },
        setup() {
            const obj = {
                age: 18,
                name: 'Tom',
            }
            const state = reactive(obj);
            const raw = toRaw(state);
            console.log('raw', raw);
            console.log(obj === raw);
            const change = () => {
                state.age = 90;
                console.log('obj', obj); // 打印原始数据obj
                console.log('state', state);  // 打印 reactive对象
            }
            return {
                state,
                change,
            }
        },
    }
</script>
<style></style>