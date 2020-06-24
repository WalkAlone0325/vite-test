<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
  <!-- <HelloWorld msg="Hello Vue 3.0 + Vite" /> -->
  <vote :title="title"></vote>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Vote from './components/Vote.vue'

export default {
  name: 'App',
  components: {
    Vote
  },
  data() {
    return {
      title: 'vue3.0好学吗？'
    }
  },
  mounted() {
    setTimeout(() => {
      this.title = 'vue还是react'
    }, 1000);
  }
}
</script>
