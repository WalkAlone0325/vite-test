<template>
  <div>
    <h3>标题：{{ title }}</h3>
    <div>
      <p>支持人数：{{ supNum }}</p>
      <p>反对人数：{{ oppNum }}</p>
      <p>支持率：{{ ratio }}</p>
      <button @click="change(0)">支持</button>
      <button @click="change(1)">反对</button>
    </div>
  </div>
</template>

<script>
import { watchEffect, ref, reactive, toRefs, computed } from 'vue'

export default {
  props: {
    title: String
  },
  // 初始化props和beforeCreate之间
  // 只渲染一次
  setup(props) {
    // props基于proxy代理的响应式数据
    // console.log(props)
    // watchEffect(() => {
    //   console.log(props.title)
    // })

    // let state = ref({
    //   supNum: 0,
    //   oppNum: 0
    // })

    // 构建响应式数据ref
    // let supNum = ref(0), oppNum = ref(0)

    // 构建响应式数据reactive
    let state = reactive({
      supNum: 0,
      oppNum: 0
    })

    // console.log(supNum.value);

    // function change(lx) {
    //   lx == 0 ? supNum.value++ : oppNum.value++
    // }

    // function change(lx) {
    //   lx == 0 ? state.value.supNum++ : state.value.oppNum++
    // }

    function change(lx) {
      lx == 0 ? state.supNum++ : state.oppNum++
    }

    // 把reactive中的每一项变为ref响应式的数据
    console.log(toRefs(state));

    let ratio = computed(() => {
      let total = state.supNum + state.oppNum
      return total === 0 ? '--' : ((state.supNum / total) * 100).toFixed(2) + '%'
    })

    return {
      ...toRefs(state),
      // state,
      // oppNum,
      // supNum,
      ratio,
      change
    }
  }
}
</script>

<style>
</style>