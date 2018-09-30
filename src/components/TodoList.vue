<template lang="pug">
  .todo
    .todo-title Todo:
    .todo-wrap
      .todo-list(v-if="todos.length")
        TodoItem(v-for="todo in todos" :key="todo.id" :todo="todo" @remove="removeTodo")
      p(v-else) Nothing left in the list. Add a new task.
    TodoProps
    //- TodoForm
</template>

<script>
import TodoItem from "./TodoItem";
import TodoProps from "./TodoProps";
import TodoForm from "./TodoForm";

let nextTodoId = 1;

export default {
  components: {
    TodoItem,
    TodoProps,
    TodoForm
  },
  name: 'TodoList',
  data () {
    return {
			newTodoText: '',
      todos: [
				{
					id: nextTodoId++,
					text: 'Learn Vue'
				},
				{
					id: nextTodoId++,
					text: 'Learn about single-file components'
				},
				{
					id: nextTodoId++,
					text: 'Fall in love'
				}
			]
    }
  },
  methods: {
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
