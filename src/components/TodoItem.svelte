<script lang="ts">
  import type { Todo } from '../types'

  interface TodoItemProps {
    todo: Todo
    toggleTodo: (id: number) => void
    deleteTodo: (id: number) => void
  }

  const { todo, toggleTodo, deleteTodo } = $props<TodoItemProps>()
</script>

<li class="flex items-center gap-2 p-3 bg-white dark:bg-slate-800 rounded-lg 
           shadow-sm border border-slate-200 dark:border-slate-700">
  <label class="flex items-center gap-3 flex-1">
    <input
      type="checkbox"
      checked={todo.completed}
      onchange={() => toggleTodo(todo.id)}
      class="w-5 h-5 rounded border-slate-300 dark:border-slate-600 
             text-blue-600 dark:text-blue-500 focus:ring-blue-500 
             dark:focus:ring-blue-400 dark:bg-slate-700"
    />
    <span class="text-slate-900 dark:text-slate-100 {todo.completed ? 'line-through text-slate-500 dark:text-slate-400' : ''}">
      {todo.text}
    </span>
  </label>
  <button
    onclick={() => deleteTodo(todo.id)}
    class="p-1 text-slate-500 hover:text-red-600 dark:text-slate-400 
           dark:hover:text-red-400 rounded-lg hover:bg-slate-100 
           dark:hover:bg-slate-700 focus:outline-none focus:ring-2 
           focus:ring-red-500 dark:focus:ring-red-400"
    aria-label="Delete todo"
  >
    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
      <path fill-rule="evenodd" d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z" clip-rule="evenodd" />
    </svg>
  </button>
</li>