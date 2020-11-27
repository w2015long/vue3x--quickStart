<template>
    <div>shallowReactive</div>
    <p>{{ shallow.a }}</p>
    <p>{{ shallow.first.b }}</p>
    <p>{{ shallow.first.second.c }}</p>
    <button @click="change1">改变第一层</button>
    <button @click="change2">改变深层</button>
</template>
<script>
    import { shallowReactive } from 'vue';

    /**
     * 只有第一层被 Proxy 处理了，也就是说只有修改第一层的值时，才会响应式更新
     * shallowReactive 监听了第一层属性的值，一旦发生改变，则更新视图
     */
    export default {
        name: 'shallowReactive',
        setup() {
            const obj = {
                a: 1,
                first: {
                    b: 2,
                    second: {
                        c: 3
                    }
                },
            }
            const shallow = shallowReactive(obj);
            console.log('shallow', shallow);
            console.log('shallow.first', shallow.first);
            console.log('shallow.first.second', shallow.first.second);
            const change1 = () => {
                shallow.a *= 10 ;
            }
            const change2 = () => {
                shallow.first.b *= 20;
                shallow.first.second.c *= 30;
                console.log(shallow);
            }
            return {
                change1,
                change2,
                shallow
            }
        }
    }
</script>