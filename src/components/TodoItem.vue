<template lang="pug">
  transition(name="fade")
    .todo-item
      .todo-item-title {{ todo.title }}
      .todo-item-proj.clearfix
        .todo-item-project-title Project:
          a.todo-item-project-link(href="#") {{ todo.project }}
        .todo-item-priority-title Priority:
          span.todo-item-priority-value {{ todo.priority }}
      transition(name="bounce")
        .todo-item-hidden-text(v-show='isShow') {{ todo.description }}
      .todo-item-props
        button.todo-item-props-change.btn(@click="$emit('add')") Change
        button.todo-item-props-close.btn(@click="$emit('remove', todo.id)") Close
        button.todo-item-props-expand.btn(@click='isShow=!isShow') {{!isShow?'Open':'Collapse'}}
</template>

<script>
export default {
  name: 'TodoItem',
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  data () {
    return {
      isShow: false
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
