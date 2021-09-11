<div align="center">
<h1>decorator-vue3.0</h1>
<p>
  <strong>vue3.0插件 装饰器.与vue2.0官方插件语法一致</strong><br>
  <strong>额外新增@computed @setup</strong>
</p>
<p>
  <sub>Made with ❤︎ by
    <a href="https://github.com/JousenZhou">JousenZhou</a>
  </sub>
</p>
<p>
<a href="https://github.com/JousenZhou/CDNPlugins-webpack"><img src="https://img.shields.io/badge/Github Page-JousenZhou-yellow" /></a>
<a href="https://github.com/JousenZhou"><img src="https://img.shields.io/badge/Author-Jousen-blueviolet" /></a>
</div>



<img align="left"   src="https://img.shields.io/badge/npm包名称-green" >vue-decorator-plus-jousenzhou

# Usage 

<img align="left"   src="https://img.shields.io/badge/example-green" >



1.以下装饰器沿用vue2.0，无改动，语法一致。

```
Prop
PropSync
Ref
Watch
WatchMounted
Emit
Inject 
Provide 
InjectReactive
ProvideReactive 
```

2.vue-class-component 的@Options  @mixins 内置进插件包

```
import { Options, mixins } from 'vue-decorator-plus-jousenzhou';
```

3.新增装饰器

@Computed

参数 : Object

```vue
<template>
    <span>{{ a }}</span>
    <span>{{ b }}</span>
</template>
<script>
import { reactive } from 'vue';
import { Options, mixins, Computed } from 'vue-decorator-plus-jousenzhou';
// 这里可以是响应式对象 或者vuex-store绑定
let object = reactive({
    a: 10,
    b: 11
});
const computed = function (keyAttrs) {
    return keyAttrs.reduce((x, y) => {
        return {
            ...x,
            [y]: {
                get: function () {
                    return object[y];
                },
                set: function (value) {
                    object[y] = value;
                }
            }
        };
    }, {});
};
@Options({
    name: 'App',
    components: {}
})
@Computed(computed(['a', 'b']))
export default class App extends mixins() {}
</script>
```

@Setup

参数 :  function | obejct

```vue
<template>
    <span>{{ a }}</span>
</template>

<script>
import { ref } from 'vue';
import { Options, mixins, Setup } from 'vue-decorator-plus-jousenzhou';
// 参数类型1 对象
let setup = {
    a: ref(10)
};
// 参数类型2 函数
let setup2 = function (prop) {
    let a = ref(10);
    return { a };
};
@Options({
    name: 'App'
})
@Setup(setup)
export default class App extends mixins() {}
</script>
```

ps: 使用了setup class内的变量声明(data) 就是无意义。



script setup       yyds

