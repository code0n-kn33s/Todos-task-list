<template lang="pug">
  .todo-form
    form(@submit="checkForm" action="/something" method="post")
      .form.clearfix
        p.form-errors(v-if="errors.length")
          b.form-errors-title Please correct the following error(s):
          ul.form-errors-list
            li.form-errors-item(v-for="error in errors") {{ error }}
        .form-item
          span Name task
          input(type="text" placeholder="Text input" name="title" id="title" v-model="title" v-focus)
        .form-item
          span Name project
          input(type="text" placeholder="Text input" name="project" id="project" v-model="project")
        .form-item.select
          select(name="priority" id="priority" v-model="priority")
            option(value="1") 1
            option(value="2") 2
            option(value="3") 3
            option(value="4") 4
        .form-item.textarea
          span Deskription
          textarea(rows="4" cols="20" wrap="hard" placeholder="Text area" name="description" id="description" v-model="description")
        .form-submit
          button.save.btn(type="submit" value="Submit") Save changes
          .cancel.btn(@click="$emit('disableForm')") Cancel 
</template>
<script>
export default {
  name: 'TodoForm',
  props: {
    todo: {
      type: Object
    }
  },
  directives: {
    focus: {
      inserted: function (el) {
        el.focus()
      }
    }
  },
  data () {
    return {
      errors:[],
      title: null,
      project: null,
      priority:1,
      description: null,
    }
  },
  methods:{
    checkForm:function(e) {
      this.errors = [];
      if(!this.title) this.errors.push("Task required.");
      if(!this.project) this.errors.push("Project required.");
      if(!this.description) this.errors.push("Description required.");
      const payload = {
        title: this.title,
        project: this.project,
        description: this.description,
        priority: this.priority,
      };
      if (!this.errors.length) this.$emit('add', payload);
      e.preventDefault();
    }
  }
}
</script>
<style lang="sass">
  .todo-form
    border: 1px solid gray
    margin-top: 10px
    .form
      padding: 10px 20px
  .form-item
    display: flex
    justify-content: flex-end
    margin-bottom: 10px
    &.textarea  
      textarea
        font-family: 'Comic'
        color: dimgray
        border-radius: 5px
        width: 300px
        font-size: 18px
        padding: 10px
        border-color: gray
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
      padding: 0 10px
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
    .cancel
      display: inline-block
  .form-errors
    display: flex
    justify-content: space-between
    margin-bottom: 15px
  .form-errors-title
    text-decoration: underline
    font-size: 18px
  .form-errors-item
    list-style: square
    color: crimson
    font-size: 18px
    margin-bottom: 5px
</style>

