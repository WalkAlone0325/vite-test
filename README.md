## vue3 新特性全面剖析

- 开发
- alpha：内部测试
- beta：公开测试
- rc：候选版本
- stable：稳定版

## 变化

1. performance
   1. 重写了虚拟 dom。跳过静态节点，只处理动态节点
   2. update 性能提高 1.3~2 倍
   3. SSR 速度提高了 2~3 倍
2. tree shaking
   1. 可以将无用的模块剪辑，仅打包需要的
3. Fragment
   1. 不再限于模块中的单个根节点
4. teleport
   1. 以前称为 portal。传送门
5. suspense
   1. 可在嵌套层级中等待嵌套的异步依赖项
6. TS
   1. 更好的 ts 支持
7. custom renderer api
   1. 自定义渲染器 api
   2. 用户可以尝试 webgl 自定义渲染器
8. `composition api`
   1. 组合式 `api`，代替原有的 `options api`
      1. 根据逻辑相关性组织代码，提高可读性和可维护性
      2. 更好的重用逻辑代码（避免 `mixins` 混入时命名冲突的问题）
   2. 但是依然可以用 `options api`
9. `proxy`
   1. 响应式不再基于 `Object.defineProperty`

## 基于 vue/cli 配置 vue3.0

`vue add vue-next`

## 基于 vite 配置 vue3.0

- 基于浏览器原生 ES imports 的开发服务器（利用浏览器去解析 imports，在服务器按需编译返回，完全跳过了打包这个概念，服务器随其随用）
- 同时不仅有 vue 文件的支持，还搞定了热更新，而且热更新的速度不会随着模块的增多而变慢

```
npm init vite-app xxx
cd xxx
npm install
npm run dev
npm run build
```

或

```
yarn create vite-app xxx
cd xxx
yarn
yarn dev
yarn build
```

## 掌握 setup 和响应式系统 api

setup 函数是一个新的组件选项，作为在组件内部使用 composit api 的入口点

- 初始化 props 和 beforeCreate 之间调用
- 可以接受 props 和 context
- this 在 setup 中不可用
  props 是响应式的，可以基于 watchEffect、watch 监听，结构赋值后则无效
