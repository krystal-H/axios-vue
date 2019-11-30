<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import axios from 'axios'

export default {
  name: 'home',
  components: {
    HelloWorld
  },
  created() {
    // localhost:8080访问的实际上是public下的index.html 所以接口直接/
    axios.get('/data.json').then(res => {
      console.log(res)
    })
  }
}
</script>
