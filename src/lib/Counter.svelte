<script>
  let count = 0
  const increment = () => {
    count += 1
  }
</script>

<button class="bg-indigo-700 text-slate-300 px-4 rounded" on:click={increment}>
  count is {count}
</button>
