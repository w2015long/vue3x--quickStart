<template>
    <h1>markRaw</h1>
    <p>{{ state.age }}</p>
    <button @click="change">改变</button>
</template>
<script>
    import { markRaw, reactive } from 'vue';
    /*
    markRaw 方法可以将原始数据标记为非响应式的，即使用 ref 或 reactive 将其包装，仍无法实现数据响应式，
    其接收一个参数，即原始数据，并返回被标记后的数据
    **/
    export default {
        name: 'markRaw',
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
            const raw = markRaw(obj);
            const state = reactive(raw);
            console.log('state', state);
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