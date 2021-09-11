<template>
    <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <span>{{ a }}</span>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import { ref } from 'vue';

import { Options, mixins, Setup } from 'vue-decorator-plus-jousenzhou';

// 参数类型1 对象
let setup = {
    a: ref(10)
};
// // 参数类型2 函数
// let setup2 = function (prop) {
//     let a = ref(10);
//     return { a };
// };
@Options({
    name: 'App',
    components: { HelloWorld }
})
@Setup(setup)
export default class App extends mixins() {}
</script>
<style lang="css">
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
