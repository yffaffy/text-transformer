<script lang="ts">
    import Button from './components/Button.svelte';
    import TextArea from './components/TextArea.svelte';
    import { fade } from 'svelte/transition';
  
    let text = $state("");
    let showNotification = $state(false);
  
    const copyToClipboard = async () => {
      try {
        await navigator.clipboard.writeText(text);
        showNotification = true;
        setTimeout(() => {
          showNotification = false;
        }, 2000);
      } catch (err) {
        console.error('Failed to copy text:', err);
      }
    };
  
    const transformText = async (type: string) => {
      switch (type) {
        case 'upper':
          text = text.toUpperCase();
          break;
        case 'lower':
          text = text.toLowerCase();
          break;
        case 'capitalize':
          text = text.split(' ')
            .map(word => word.charAt(0).toUpperCase() + word.slice(1).toLowerCase())
            .join(' ');
          break;
        case 'removeDuplicates':
          text = text.split(' ')
            .filter((word, index, array) => array.indexOf(word) === index)
            .join(' ');
          break;
        case 'clear':
          text = '';
          return; // Don't copy to clipboard when clearing
      }
      
      if (text) {
        await copyToClipboard();
      }
    };
  </script>
  
  <div class="text-transformer">
    <TextArea
      bind:value={text}
      placeholder="Enter or paste your text here..."
    />
    
    <div class="actions">
      <Button variant="secondary" on:click={() => transformText('upper')}>
        UPPERCASE
      </Button>
      <Button variant="secondary" on:click={() => transformText('lower')}>
        lowercase
      </Button>
      <Button variant="secondary" on:click={() => transformText('capitalize')}>
        Capitalize
      </Button>
      <Button variant="secondary" on:click={() => transformText('removeDuplicates')}>
        🚫 Duplicates
      </Button>
      <Button variant="danger" on:click={() => transformText('clear')}>
        Clear
      </Button>
    </div>
  
    {#if showNotification}
      <div class="notification" transition:fade>
        Copied to clipboard!
      </div>
    {/if}
  </div>
  
  <style>
    .text-transformer {
      display: flex;
      flex-direction: column;
      gap: 1rem;
      width: 100%;
      position: relative;
    }
  
    .actions {
      display: flex;
      gap: 0.5rem;
      flex-wrap: wrap;
    }
  
    .notification {
      position: absolute;
      bottom: -40px;
      left: 50%;
      transform: translateX(-50%);
      background-color: #10b981;
      color: white;
      padding: 0.5rem 1rem;
      border-radius: 4px;
      font-size: 0.875rem;
      box-shadow: 0 1px 2px 0 rgb(0 0 0 / 0.1);
    }
  
    @media (max-width: 480px) {
      .actions {
        flex-direction: column;
      }
    }
  
    @media (prefers-color-scheme: dark) {
      .notification {
        background-color: #059669;
      }
    }
  </style>