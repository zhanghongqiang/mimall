<template>
  <div id="app">
    <router-view>
    </router-view>
  </div>
</template>

<script>


export default {
  name: 'App',
  methods: {
    gerUser(){
      this.axios.get('/user').then((res = {}) => {
        this.$store.dispatch('saveUserName', res.username)
      })
    },
    getCartCount(){
      this.axios.get('/carts/products/sum').then( (res = 0) => {
        this.$store.dispatch('saveCartCount', res)
      })
    } 
  },
}
</script>

<style lang="sass">
@import "./assets/sass/reset"
</style>
