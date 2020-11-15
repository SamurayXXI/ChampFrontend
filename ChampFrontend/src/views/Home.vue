<template>
  <div class="home">
    <Championships msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import Championships from '@/components/Championships.vue'

export default {
  name: 'Home',
  components: {
    Championships
  }
}
</script>
