<template lang="pug">
  .todo-props
      button.todo-props-create.btn New task
      .todo-props-sort.checkbox_block
        .label
          label(for="remember") By Priority
            input#remember.invisible(type="checkbox")
            .checkbox
              svg(width="20px" height="20px" viewBox="0 0 20 20")
                path(d="M3,1 L17,1 L17,1 C18.1045695,1 19,1.8954305 19,3 L19,17 L19,17 C19,18.1045695 18.1045695,19 17,19 L3,19 L3,19 C1.8954305,19 1,18.1045695 1,17 L1,3 L1,3 C1,1.8954305 1.8954305,1 3,1 Z")
                polyline(points="4 11 8 15 16 6")
      .todo-props-select.custom-select
        button.select-group.btn All 
          span.triangle &#9660;
        .todo-props-select-list
          .todo-props-select-item
            input(type="radio" name="proj-group" id="all-proj")
            label(for="all-proj") All
          .todo-props-select-item
            input(type="radio" name="proj-group" id="proj1")
            label(for="proj1") Project 1
          .todo-props-select-item
            input(type="radio" name="proj-group" id="proj2")
            label(for="proj2") Project 2
</template>

<script>
  export default {
    name: 'TodoProps'
  }
</script>

<style lang="sass">
.todo-props
  margin-top: 10px
  display: flex
  justify-content: space-between

.todo-props-create
  height: 40px

.todo-props-select-list
  border: 1px solid gray
  border-radius: 5px
  padding: 5px 15px
  margin-top: 5px

.select-group .triangle
  font-size: 10px
  margin-left: 6px
</style>
