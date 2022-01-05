<template>
  <Welcome :user="user" :msg2="100" />
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Welcome from './components/Welcome.vue'
import Yahoo from './components/Yahoo.vue'

type Person = {
  firstName: string;
  lastName: string;
  age: number;
};

export default defineComponent({
  name: 'App',
  components: {
    Welcome
  },

  data () {
    return {
      person: {
        firstName: '田中',
        lastName: '健',
        age: 38
      } as Person
    }
  },

  computed: {
    user (): Person {
      return this.person
    }
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
