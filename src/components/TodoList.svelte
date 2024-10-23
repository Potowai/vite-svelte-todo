<script lang="ts">
  import TodoItem from './TodoItem.svelte'
  import type { Todo } from '../types'

  interface TodoListProps {
    todos: Todo[]
    toggleTodo: (id: number) => void
    deleteTodo: (id: number) => void
  }

  const { todos, toggleTodo, deleteTodo } = $props<TodoListProps>()
</script>

{#if todos.length === 0}
  <p class="text-center text-slate-600 dark:text-slate-400 italic">
    No todos yet! Add some tasks above.
  </p>
{:else}
  <ul class="space-y-2">
    {#each todos as todo (todo.id)}
      <TodoItem {todo} {toggleTodo} {deleteTodo} />
    {/each}
  </ul>
{/if}