<template lang="pug">
  #app
    Todo

</template>

<script>
  import Todo from './components/Todo'

  export default {
    name: 'app',
    components: {
      Todo
    }
  }
</script>

<style lang="sass">
  @import './style/assets/reset.sass'
  @import './style/assets/fonts.sass'
  @import './style/elems/checkbox.sass'
  @import './style/elems/radio.sass'
  @import './style/common.sass'
</style>
