<template lang="pug">
  .todo
    .todo-title Todo:
    .todo-wrap
      .todo-list(v-if="todos.length")
        TodoItem(v-for="todo in todos" :key="todo.id" :todo="todo" @remove="removeTodo" @add="showTodoForm=!showTodoForm")
      p(v-else) Nothing left in the list. Add a new task.
    TodoProps( v-if="showTodoForm" @add="showTodoForm=!showTodoForm")
    TodoForm( v-else @add="showTodoForm=!showTodoForm")
</template>

<script>
import TodoItem from "./TodoItem";
import TodoProps from "./TodoProps";
import TodoForm from "./TodoForm";

let nextTodoId = 1;

export default {
  name: 'TodoList',
  components: {
    TodoItem,
    TodoProps,
    TodoForm
  },
  name: 'TodoList',
  data () {
    return {
      newTodoText: '',
      showTodoForm: true,
      todos: [
        {
          id: nextTodoId++,
          title: 'Learn Vue',
          priority: 1,
          project: 'Project 1'
				},
				{
					id: nextTodoId++,
          title: 'Learn about single-file components',
          priority: 2,
          project: 'Project 2'
				}
			]
    }
  },
  methods: {
    openTodoForm () {
      console.log(this.showTodoForm);
    },
		addTodo () {
			const trimmedText = this.newTodoText.trim()
			if (trimmedText) {
				this.todos.push({
					id: nextTodoId++,
					text: trimmedText
				})
				this.newTodoText = ''
			}
		},
		removeTodo (idToRemove) {
			this.todos = this.todos.filter(todo => {
				return todo.id !== idToRemove
			})
    },
    selectProject () {
      console.log(this);
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
  height: 450px
  border: 1px solid gray
  padding: 15px
  overflow-y: scroll
</style>
