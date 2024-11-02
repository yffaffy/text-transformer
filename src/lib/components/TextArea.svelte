<script lang="ts">
  let { value = $bindable(), placeholder = '', rows = 8 } = $props();
</script>

<textarea
  bind:value
  {placeholder}
  {rows}
  class="text-area"
></textarea>
  
<style>
  .text-area {
    width: 100%;
    padding: 0.75rem;
    border: 1px solid #e2e8f0;
    border-radius: 4px;
    font-size: 0.875rem;
    background-color: #fff;
    color: #0f172a;
    resize: vertical;
    font-family: inherit;
    transition: border-color 0.2s;
  }

  .text-area:focus {
    outline: none;
    border-color: #0f172a;
  }

  @media (prefers-color-scheme: dark) {
    .text-area {
      background-color: #1e293b;
      border-color: #334155;
      color: #fff;
    }

    .text-area:focus {
      border-color: #60a5fa;
    }
  }
</style>