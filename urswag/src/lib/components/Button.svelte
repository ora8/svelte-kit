<script lang="ts">
    import { type Snippet } from "svelte";

    interface ButtonProps {
        children: Snippet;
        className?: string;
        onClick?: () => void;
    }

    let { children, className, onClick, ...props }: ButtonProps = $props()   ;
</script>

<button class="btn {className}" onclick={onClick} {...props}>
    {@render children()}
</button>

<style>
    .btn {
        padding: 0.5em 1em;
        border: none;
        border-radius: 4px;
        background-color: #34ab62;
        color: white;
        cursor: pointer;
        font-size: 1em;
        transition: background-color 0.3s ease;
    }

    .btn:hover {
        background-color: #20d438;
    }

    .btn:active {
        background-color: #10dc65;
    }

    .btn:disabled {
        background-color: #6c757d;
        cursor: not-allowed;
    }
</style>