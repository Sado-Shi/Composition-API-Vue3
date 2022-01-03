<template>
  <div>
    <h3>{{ hello.title }}</h3>
    <p>{{ snippet }}</p>
  </div>
</template>

<script lang="ts">
import { computed } from 'vue'

export default {
  props: {
    hello: {}
  },

  setup (props) {
    const snippet = computed(() => {
      return props.hello.body.substring(0, 10) + '...'
    })

    return { snippet }
  }
}
</script>
