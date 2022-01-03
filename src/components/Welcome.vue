<template>
  <div class="welcome">
    <h1>{{ msg }}</h1>
    <button @click="changeMsg('msg!')">Click!</button>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'Welcome',

  data () {
    return {
      msg: 'Hello!TypeScript!'
    }
  },

  computed: {
    getLength (): number {
      return this.msg.length
    }
  },

  methods: {
    changeMsg (msg: string) {
      this.msg = msg
    }
  }

  // setup () {
  //   const msg = 'Hello!'

  //   const getLength: string = computed(() => {
  //     return msg
  //   })

  //   return { msg, getLength }
  // }
})
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
