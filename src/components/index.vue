<template>
  <div>
    <main-header></main-header>
    <main-body></main-body>
    <main-footer></main-footer>
  </div>
</template>

<script>
  import Header from  './todos/header'
  import Footer from './todos/footer'
  import Body from './todos/body'
  export default {
    name: 'hello',
    data () {
      return {
        msg: 'Welcome to Your Vue.js App',
      }
    },
    components: {
      ["main-header"]: Header,
      ['main-body']: Body,
      ['main-footer']: Footer
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="stylus" scoped>
  a
    color #42b983
</style>
