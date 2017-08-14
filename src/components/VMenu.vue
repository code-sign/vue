<template>
    <div>
      <!-- Template 에 최상위 태그가 1개만 있어야 렌더가 가능 -->
      <h1>Vue.js</h1>
      <ul>
        <li><v-link href="./">Home</v-link></li>
        <li><v-link href="./about">About</v-link></li>
        <li><v-link href="./work">Work</v-link></li>
        <li><v-link href="./contact">Contact</v-link></li>
      </ul>
    </div>
</template>

<script>
  import routes from '../routes'
  import VLink from '../components/VLink.vue'

  export default {
    components: {
      VLink
    }
  }
</script>

<style scoped>
  ul{
    border:1px solid #ccc;
  }

</style>
