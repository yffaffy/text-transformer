<script lang="ts">
  import TextTransformer from './lib/TextTransformer.svelte';
</script>

<main>
  <div class="container">
    <header>
      <h1>Text Transformer</h1>
      <p>Paste and click. Transformed text is automatically copied to your clipboard.</p>
    </header>
    <TextTransformer />
  </div>
</main>

<style>
  main {
    min-height: 100vh;
    display: flex;
    align-items: center;
    padding: 1rem;
  }

  .container {
    width: 100%;
    max-width: 640px;
    margin: 0 auto;
    background-color: #fff;
    border-radius: 8px;
    box-shadow: 0 1px 3px 0 rgb(0 0 0 / 0.1);
    padding: 2rem;
  }

  header {
    margin-bottom: 2rem;
  }

  h1 {
    font-size: 1.5rem;
    font-weight: 600;
    margin: 0;
    color: #0f172a;
  }

  p {
    margin: 0.5rem 0 0;
    color: #64748b;
    font-size: 0.875rem;
  }

  @media (prefers-color-scheme: dark) {
    .container {
      background-color: #0f172a;
      box-shadow: 0 1px 3px 0 rgb(0 0 0 / 0.3);
    }

    h1 {
      color: #fff;
    }

    p {
      color: #94a3b8;
    }
  }

  @media (max-width: 480px) {
    .container {
      padding: 1.5rem;
    }
  }
</style>