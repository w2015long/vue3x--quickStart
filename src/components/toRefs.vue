<template>
    <div>{{ state.name.value }}</div>
</template>
<script>
    /*
    返回的是一个对象，对象里包含了每一个包装过后的响应式数据对象
     */
    import { toRefs } from 'vue';
    export default {
        name: 'toRefs',
        props: {
            range: {
                type: Number,
                default: 10
            }
        },
        setup() {
            const obj = {
                name: 'Tom',
                age: 18,
            }
            const state = toRefs(obj);
            console.log(state.name.value);
            return {
                state,
            }
        },
    }
</script>
<style></style>