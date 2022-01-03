<template>
  <HelloWorld v-if="showHellos" :hellos="hellos" />
  <button @click="showHellos = !showHellos">表示/非表示</button>
  <button @click="hellos.pop()">delete</button>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import HelloWorld from './components/HelloWorld.vue'

export default defineComponent({
  name: 'App',
  components: {
    HelloWorld
  },

  setup () {
    const hellos = ref([
      {
        title: 'ようこそハロー',
        body: 'これはボディの内容です',
        id: 1
      },
      {
        title: 'title2',
        body: 'Lorem ipsum',
        id: 2
      }
    ])

    const showHellos = ref(true)

    return { hellos, showHellos }
  }
})
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
