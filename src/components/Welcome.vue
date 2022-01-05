<template>
  <div class="welcome">
    <h1>{{ msg }}</h1>
    <button @click="changeMsg('msg!')">Click!</button>
    <h1>{{ book.title }}/{{ book.author }}/{{ book.year }}</h1>
    <h2>{{ msg2 }}</h2>

    <h1>{{ fullName }} {{ user.age }}</h1>
  </div>

  <div>
    <Yahoo :user="user" :msg2="msg2" />
  </div>
</template>

<script lang="ts">
import { computed, defineComponent, ref, PropType } from 'vue'
import Yahoo from '@/components/Yahoo.vue'

interface Book {
  title: string;
  author: string;
  year: number;
}

export interface User {
  firstName: string;
  lastName: string;
  age: number;
}

// type Hp = number;
// const Pokemon: Hp = '200'

type POKEMON = 'zenigame' | 'hitokage' | 'atyamo';
const get: POKEMON = 'zenigame'
console.log(get)

export default defineComponent({
  name: 'Welcome',

  components: {
    Yahoo
  },

  props: {
    msg2: {
      type: Number as PropType<number>
    },
    user: {
      type: Object as PropType<User>,
      required: true
    }
  },

  data () {
    return {
      book: {
        title: 'Vue 3 Guide',
        author: 'Vue Team',
        year: 2020
      } as Book,

      msg: 'Hello!TypeScript!'
    }
  },

  computed: {
    getLength (): number {
      return this.msg.length
    },

    fullName (): string {
      return this.user.firstName + ' ' + this.user.lastName
    }
  },

  methods: {
    changeMsg (msg: string): string {
      this.msg = msg
      this.book.year = 2020
      return msg
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
