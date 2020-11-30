<template>
    <h2>shallowRef</h2>
    <p>{{ shallow.a }}</p>
    <p>{{ shallow.first.b }}</p>
    <p>{{ shallow.first.second.c }}</p>
    <button @click="change1">change1</button>
    <br>
    <br>
    <br>
    <button @click="change2">change2</button>
</template>
<script>
    import { shallowRef, triggerRef } from 'vue';

    /**
     * shallowRef .value 重新赋值了，视图就立马更新了
     * 改变单个 某个值 视图不会更新 需要triggerRef 视图才会更新
     */
    export default {
        name: 'shallowRef',
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
            const shallow = shallowRef(obj);
            console.log('shallow1', shallow);
            const change1 = () => {
                shallow.value = {
                    a: 11,
                    first: {
                        b: 22,
                        second: {
                            c: 33
                        }
                    },
                }
                console.log('shallow.value', shallow);
            }
            const change2 = () => {
                shallow.value.first.b = 8;
                shallow.value.first.second.c = 9;
                console.log('shallow 前', shallow);
                triggerRef(shallow);
                console.log('shallow 后', shallow);
            }
            return {
                change1,
                change2,
                shallow
            }
        }
    }
</script>