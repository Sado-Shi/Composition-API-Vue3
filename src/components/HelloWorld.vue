<template>
  <div>
    <h1>Home</h1>
    <div v-for="hello in hellos" :key="hello.id">
      <HelloJapan :hello="hello" />
      <!-- <h2>{{ hello.title }}</h2> -->
    </div>
    <!-- <p ref="p">私の名前は{{ name }}です。{{ age }}歳です。</p>
    <button @click="handleClick">Change!</button>
    <p>私の名前は{{ student.name2 }}です。{{ student.age2 }}歳です</p>
    <button @click="handleClickTwo">Change2!</button> -->
    <!-- <button @click="age++">年齢を上げる</button>
    <button @click="age--">年齢を下げる</button> -->
    <!-- <input type="text" v-model="name"> -->
    <!-- <input type="text" v-model="search">
    <p>検索 - {{ search }}</p>
    <div v-for="name in matchingNames" :key="name">{{ name }}</div>
    <button @click="handleClick">stop!</button> -->
  </div>
</template>

<script lang="ts">
import {
  defineComponent, ref, reactive, computed, watch, watchEffect, onMounted, onUnmounted, onUpdated
} from 'vue'

import HelloJapan from '@/components/HelloJapan.vue'

export default defineComponent({
  name: 'HelloWorld',
  props: {
    hellos: {}
  },
  components: {
    HelloJapan
  },

  setup (props) {
    console.log(props.hellos)

    const search = ref('')
    const names = ref([
      '山田',
      '佐々木',
      '武田',
      '内山',
      '花田',
      '山岡',
      '近藤',
      '吉川'
    ])

    const stopWatch = watch(search, () => [
      console.log('watch function route')
    ])

    const stopEffect = watchEffect(() => {
      console.log('watch function run', search.value)
    })

    const handleClick = () => {
      stopWatch()
      stopEffect()
    }

    const matchingNames = computed(() => {
      // console.log(names.value.filter(name => name.includes('')))
      // console.log(search.value)
      return names.value.filter(name => name.includes(search.value))
    })
    // // ref
    // const name = ref('北川')
    // const age = ref(27)

    // // reactive
    // const student = reactive({ name2: '沖縄', age2: 20 })

    // // ref
    // const handleClick = () => {
    //   name.value = '深沢'
    //   age.value = 55
    // }

    // // reactive
    // const handleClickTwo = () => {
    //   student.name2 = '北道'
    //   student.age2 = 80
    // }
    // return { name, age, handleClick, student, handleClickTwo }
    onMounted(() => console.log('component mounted'))
    onUnmounted(() => console.log('component unmounted'))
    onUpdated(() => console.log('component updated'))

    return { matchingNames, search, names, handleClick }
  }
})
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
