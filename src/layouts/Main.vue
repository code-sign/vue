<template>
  <div class="container">
    <p>이 페이지는 메인 레이아웃 적용</p>  
    <v-menu></v-menu>
    <slot></slot>

  </div>
</template>

<script>
  import VLink from '../components/VLink.vue'
  import VMenu from '../components/VMenu.vue'

  export default {
    components: {
      VLink,
      VMenu
    }
  }
</script>

<style scoped>
  .container {
    max-width: 600px;
    margin: 0 auto;
    padding: 15px 30px;
    border:3px solid royalblue;
  }
</style>
