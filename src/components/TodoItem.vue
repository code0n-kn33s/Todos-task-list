<template lang="pug">
  .todo-item
    .todo-item-title Title of the task
    .todo-item-proj.clearfix
      .todo-item-project-title Project:
        a.todo-item-project-link(href="#") Project!
      .todo-item-priority-title Priority:
        span.todo-item-priority-value 1
    .todo-item-hidden-text.
      Lorem ipsum, dolor sit amet consectetur adipisicing elit. At aliquam ipsa blanditiis ea delectus, et numquam non, eos, fuga. Porro.
    .todo-item-props
      button.todo-item-props-change.btn Change
      button.todo-item-props-close.btn Close
      button.todo-item-props-expand.btn Collapse
</template>

<script>
  export default {
    name: 'TodoItem',
    props: {
      title: Number
    },
    methods: {
      collapseTodo () {
        const trimmedText = this.newTodoText.trim()
        if (trimmedText) {
          this.todos.push({
            id: nextTodoId++,
            text: trimmedText
          })
          this.newTodoText = ''
        }
      },
      removeTodo () {
        const trimmedText = this.newTodoText.trim()
        if (trimmedText) {
          this.todos.push({
            id: nextTodoId++,
            text: trimmedText
          })
          this.newTodoText = ''
        }
      }
	  }
  }
</script>

<style lang="sass">
.todo-item
  padding: 15px 25px
  background-color: #fbfbfb
  border: 1px solid gray
  margin-bottom: 10px

.todo-item-title
  font-size: 26px
  margin-bottom: 10px

.todo-item-proj
  margin-bottom: 15px

.todo-item-project-title
  float: left

.todo-item-priority-title
  float: right

.todo-item-hidden-text
  margin-bottom: 20px

.todo-item-props
  display: flex
  justify-content: space-between

</style>
