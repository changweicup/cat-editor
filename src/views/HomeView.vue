<template>
  <div class="home">
    <div class="editor-wrap" id="editor-wrap">
      <HelloWorld v-model="content" />
    </div>
    <div>{{content}}</div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld
  },
  data () {
    return {
      content: ''
    }
  }
}
</script>
