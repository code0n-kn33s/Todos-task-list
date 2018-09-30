<template lang="pug">
  #app
    TodoList

</template>

<script>
  import TodoList from './components/TodoList'

  export default {
    name: 'app',
    components: {
      TodoList
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
