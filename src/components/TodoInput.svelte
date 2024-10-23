<script lang="ts">
  interface TodoInputProps {
    addTodo: (text: string) => void
  }

  const { addTodo } = $props<TodoInputProps>()
  let newTodoText = $state('')

  function handleSubmit() {
    if (newTodoText.trim()) {
      addTodo(newTodoText.trim())
      newTodoText = ''
    }
  }
</script>

<div class="mb-8">
  <div class="flex gap-2">
    <input
      type="text"
      placeholder="What needs to be done?"
      bind:value={newTodoText}
      onkeydown={(e) => e.key === 'Enter' && handleSubmit()}
      class="flex-1 px-4 py-2 rounded-lg border border-slate-300 dark:border-slate-600 
             bg-white dark:bg-slate-800 text-slate-900 dark:text-slate-100
             focus:outline-none focus:ring-2 focus:ring-blue-500 dark:focus:ring-blue-400"
    />
    <button
      onclick={handleSubmit}
      class="px-4 py-2 bg-blue-600 hover:bg-blue-700 dark:bg-blue-500 dark:hover:bg-blue-600
             text-white font-medium rounded-lg focus:outline-none focus:ring-2 
             focus:ring-blue-500 focus:ring-offset-2 dark:focus:ring-offset-slate-800"
    >
      Add
    </button>
  </div>
</div>