<template>
  <div>
  <h1> Hello World VueJS</h1>

    <CcIntro></CcIntro>
  </div>
</template>

<script>
import CcIntro from './Intro.vue'
export default {
  components : {
    CcIntro
  }
}
</script>

<style scoped>
 h1{
   font-size: 58px
 }
</style>
