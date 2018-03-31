<template>
 <v-app id="app">
   <CPMenu></CPMenu>
   <v-content>
      <v-container fluid fill-height>
        <router-view></router-view>
      </v-container>
    </v-content>
 </v-app>
</template>

<script>
import CPMenu from './components/root/menu.vue'
export default {
  components: {
    CPMenu
  }
}
</script>
