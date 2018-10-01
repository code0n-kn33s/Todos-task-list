<template lang="pug">
  .todo
    .todo-title Todo:
    .todo-wrap
      .todo-list(v-if="todos.length")
        TodoItem(v-for="todo in todos" :key="todo.id" :todo="todo" @remove="removeTodo" @changeForm="changeCurent" v-show="todo.visible")
      p(v-else) Nothing left in the list. Add a new task.
    TodoForm(v-if="showTodoForm" @disableForm="showTodoForm=!showTodoForm" @add="addTodo")
    .todo-props(v-else)
      button.todo-props-create.btn(@click="showTodoForm=!showTodoForm") New task
      .todo-props-sort.checkbox_block
        .label(@click="checkedPriority")
          label(for="remember") By Priority
            input#remember.invisible(type="checkbox")
            .checkbox
              svg(width="20px" height="20px" viewBox="0 0 20 20")
                path(d="M3,1 L17,1 L17,1 C18.1045695,1 19,1.8954305 19,3 L19,17 L19,17 C19,18.1045695 18.1045695,19 17,19 L3,19 L3,19 C1.8954305,19 1,18.1045695 1,17 L1,3 L1,3 C1,1.8954305 1.8954305,1 3,1 Z")
                polyline(points="4 11 8 15 16 6")
      .todo-props-select.custom-select
        button.select-group.btn(@click="selectProject=!selectProject") {{picked}}
          span.triangle &#9660;
        transition(name="fade")
          ul.todo-props-select-list(v-show="selectProject") 
            li.todo-props-select-item
              input(type="radio" name="proj-group" id="all-proj" value="All" checked="checked" v-model="picked" )
              label(for="all-proj" @click="pickedProjectAll") All
            li.todo-props-select-item(v-for="todoProj in todos" )
              input(type="radio" name="proj-group" :id="todoProj.id" :value="todoProj.project" v-model="picked")
              label(:for="todoProj.id" @click="pickedProject(todoProj.id)") {{ todoProj.project }}
</template>

<script>
import TodoItem from "./TodoItem";
import TodoForm from "./TodoForm";

let nextTodoId = 1;

export default {
  name: 'TodoList',
  components: {
    TodoItem,
    TodoForm
  },
  data () {
    return {
      newTodoText: '',
      selectProject: false,
      showTodoForm: false,
      checked: false,
      picked: 'All',
      todos: [
        {
          id: nextTodoId++,
          visible: true,
          title: 'Parsing dom',
          project: 'Project 3',
          priority: 3,
          description: 'Lorem ipsum, dolor sit amet consectetur adipisicing elit. At aliquam ipsa blanditiis ea delectus, et numquam non, eos, fuga. Porro.'
				},
        {
          id: nextTodoId++,
          visible: true,
          title: 'Learn Vue',
          project: 'Project 1',
          priority: 1,
          description: 'Lorem ipsum, dolor sit amet consectetur adipisicing elit. At aliquam ipsa blanditiis ea delectus, et numquam non, eos, fuga. Porro.'
				},
				{
          id: nextTodoId++,
          visible: true,
          title: 'Learn about single-file components',
          project: 'Project 2',
          priority: 2,
          description: 'Lorem ipsum, dolor sit amet consectetur adipisicing elit. At aliquam ipsa blanditiis ea delectus, et numquam non, eos, fuga. Porro.'
				}
      ]
    }
  },
  methods: {
		addTodo (todo) {
      this.todos.push({
        id: nextTodoId++,
        title: todo.title,
        project: todo.project,
        priority: todo.priority,
        description: todo.description
      });
      this.showTodoForm=true;

		},
		removeTodo (idToRemove) {
			this.todos = this.todos.filter(todo => {
				return todo.id !== idToRemove
			})
    },
    checkedPriority() {
      this.todos.sort(function(a, b) { 
        return a.priority > b.priority ? 1 : -1; 
      }); 
    },
    pickedProject(id) {
      this.todos.filter(todo => {
        todo.visible = true;
        if(todo.id !== id) todo.visible = false
      });
    },
    pickedProjectAll() {
      this.todos.filter(todo => {
        todo.visible = true;
      });
    },
    changeCurent() {
      console.log('change');
    }
  }
}
</script>

<style lang="sass">
.todo 
  width: 500px
  margin: 10px auto

.todo-title 
  text-align: center
  font-size: 35px

.todo-wrap 
  margin-top: 10px
  height: 420px
  border: 1px solid gray
  padding: 15px
  overflow-y: scroll
.todo-props
  display: flex
  position: relative
  margin-top: 10px
  justify-content: space-between

.todo-props-create
  height: 40px

.todo-props-select-list
  position: absolute
  right: 0
  border: 1px solid gray
  border-radius: 5px
  padding: 5px 15px
  margin-top: 5px

.select-group .triangle
  font-size: 10px
  margin-left: 6px
</style>
