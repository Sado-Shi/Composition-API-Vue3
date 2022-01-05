<script lang="ts">
import { computed, defineComponent, ref, PropType, reactive, toRefs } from 'vue'

interface State {
  msg3: string,
  msg4: string
}

export interface User {
  firstName: string;
  lastName: string;
  age: number;
}

export default defineComponent({
  name: 'Yahoo',
  props: {
    msg2: {
      type: Number as PropType<number>
    },
    user: {
      type: Object as PropType<User>,
      required: true
    }
  },

  setup () {
    const state = reactive<State>(
      {
        msg3: 'Yahoo!!',
        msg4: 'message4!'
      }
    )

    return {
      ...toRefs(state)
    }
  }
})
</script>

<template>
  <div>
    <h1>{{ msg3 }}</h1>
    <h1>{{ msg4 }}</h1>
    <h1>{{ msg2 }}</h1>
  </div>
</template>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
