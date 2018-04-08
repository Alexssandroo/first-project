<template>
  <div>
      <h2>Dashboard</h2>
  </div>
</template>
<script>
import http from '../../../http'
export default {
  mounted () {
    http.get('https://pokeapi.co/api/v2/pokemon/2/')
      .then(response => response.data)
      .then(data => {
        console.log(data)
      })
  }
}
</script>
