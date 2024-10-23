<script lang="ts">
  import type { Todo } from './types'
  import TodoInput from './components/TodoInput.svelte'
  import TodoList from './components/TodoList.svelte'

  let todos: Todo[] = $state([])
  let nextId = $state(1)

  function addTodo(text: string) {
    todos = [...todos, { id: nextId, text, completed: false }]
    nextId++
  }

  function toggleTodo(id: number) {
    todos = todos.map(todo =>
      todo.id === id ? { ...todo, completed: !todo.completed } : todo
    )
  }

  function deleteTodo(id: number) {
    todos = todos.filter(todo => todo.id !== id)
  }
</script>

<main class="min-h-screen bg-slate-50 dark:bg-slate-900 py-8 px-4">
  <div class="max-w-2xl mx-auto">
    <h1 class="text-3xl font-bold text-slate-900 dark:text-white mb-8 text-center">
      Todo List
    </h1>
    <TodoInput {addTodo} />
    <TodoList {todos} {toggleTodo} {deleteTodo} />
  </div>
</main>