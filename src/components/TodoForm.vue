<template lang="pug">
  .todo-form
    form.clearfix
      .form-item
        span Name task
        input(type="text" placeholder="Text input")
      .form-item
        span Name project
        input(type="text" placeholder="Text input")
      .form-item.select
        select
          option(value="1") 1
          option(value="2") 2
          option(value="3") 3
          option(value="4") 4
      .form-item.textarea
        span Deskription
        input(type="textarea" placeholder="Text area")
      .form-submit
        button.save.btn(type="submit") Save changes
        button.cancel.btn Cancel 
</template>
<script>
export default {
  name: 'TodoForm'
}
</script>
<style lang="sass">
  .todo-form
    border: 1px solid gray
    margin-top: 10px
    form
      padding: 10px 20px
  .form-item
    display: flex
    justify-content: flex-end
    margin-bottom: 10px
    &.textarea
      height: 100px
    &.select
      select
        font-family: 'Comic'
        width: 300px
        font-size: 18px
        background: none
        color: dimgray
    span
      margin-right: 15px
    input
      display: inline-block
      width: 300px
      border-radius: 5px
      padding: 0 5px
      font-size: 18px
      font-family: 'Comic'
      color: dimgray
  .form-submit
    width: 300px
    float: right
    button
      display: inline-block
    .save
      margin-right: 30px

</style>

