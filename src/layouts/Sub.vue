<template>
  <div class="container">
    <p>이 페이지는 서브레이아웃 적용</p>
    <v-menu></v-menu>
    <sub-top></sub-top>
    <slot></slot>

  </div>
</template>

<script>
  import VLink from '../components/VLink.vue'
  import VMenu from '../components/VMenu.vue'  
  import SubTop from '../components/SubTop.vue'

  export default {
    components: {
      VLink,
      VMenu,
      SubTop
    }
  }
</script>

<style scoped>
  .container {
    max-width: 600px;
    margin: 0 auto;
    padding: 15px 30px;
    border:3px solid #aaa;
  }
</style>
