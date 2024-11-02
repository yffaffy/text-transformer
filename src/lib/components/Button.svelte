<script lang="ts">
    export let variant: 'primary' | 'secondary' | 'danger' = 'primary';
    export let type: 'button' | 'submit' | 'reset' = 'button';
</script>

<button {type} class="btn {variant}" on:click>
<slot />
</button>

<style>
    .btn {
        padding: 0.625rem 1rem;
        border: none;
        border-radius: 4px;
        font-size: 0.875rem;
        font-weight: 500;
        cursor: pointer;
        transition: background-color 0.2s;
        min-width: 100px;
    }

    .primary {
        background-color: #0f172a;
        color: #fff;
    }

    .primary:hover {
        background-color: #1e293b;
    }

    .secondary {
        background-color: #e2e8f0;
        color: #0f172a;
    }

    .secondary:hover {
        background-color: #cbd5e1;
    }

    .danger {
        background-color: #ef4444;
        color: #fff;
    }

    .danger:hover {
        background-color: #dc2626;
    }

    @media (prefers-color-scheme: dark) {
        .secondary {
        background-color: #334155;
        color: #fff;
        }

        .secondary:hover {
        background-color: #475569;
        }
    }
</style>