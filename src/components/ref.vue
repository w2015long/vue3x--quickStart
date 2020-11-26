<template>
    <div>{{ num }}</div>
    <button @click="add">增加</button>
</template>
<script>
    import { ref } from 'vue';
    /*
    * 基本类型值（String 、Nmuber 、Boolean 等）或单值对象（类似像 {count: 3} 这样只有一个属性值的对象）使用 ref
    *引用类型值（Object 、Array）使用 reactive
    **/
    export default {
        name: 'ref',
        props: {
            range: {
                type: Number,
                default: 10
            }
        },
        setup(props) {
            let num = ref(0);
            const add = () => {
                if (num.value === props.range) {
                    alert('超出最大值');
                } else {
                    num.value++;
                }
            }
            return {
                num,
                add,
            }
        },
    }
</script>
<style></style>