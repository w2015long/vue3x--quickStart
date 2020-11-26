<template>
    <p>{{ refNum }}</p>
    <button @click="addRef">ref--增加</button>
    <br>
    <br>
    <p>{{ toRerNum }}</p>
    <button @click="addToRef">toRef--增加</button>
</template>
<script>
    import { ref, toRef } from 'vue';
    /*
    ref 是对传入数据的拷贝；
    toRef 是对传入数据的引用
    ref 的值改变会更新视图；
    toRef 的值改变不会更新视图
    **/
    export default {
        name: 'refAndToRef',
        props: {
            range: {
                type: Number,
                default: 10
            }
        },
        setup(props) {
            const obj = { count: 1 }
            const refNum = ref(obj.count);
            const toRerNum = toRef(obj, 'count');
            const addRef = () => {
                if (refNum.value === props.range) {
                    alert('超出最大值');
                } else {
                    refNum.value++;
                    console.log('原始值：', obj);
                    console.log('响应式数据对象：', refNum);
                }
            }
            const addToRef = () => {
                if (toRerNum.value === props.range) {
                    alert('超出最大值');
                } else {
                    toRerNum.value++;
                    console.log('原始值：', obj);
                    console.log('响应式数据对象：', toRerNum);
                }
            }
            return {
                refNum,
                toRerNum,
                addRef,
                addToRef,
            }
        },
    }
</script>
<style></style>