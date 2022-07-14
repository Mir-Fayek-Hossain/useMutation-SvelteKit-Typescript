<script lang="ts">
    import { useMutation } from '@sveltestack/svelte-query';
    const mutation = useMutation((newTodo:any) =>
        fetch(url, {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json'
            },
            body: JSON.stringify(newTodo)
        })
    );
    const url = ' https://jsonplaceholder.typicode.com/todos';
    let title = '';
    const onSubmit = () => {
        $mutation.mutate({ userId: 1, title });
        title = '';
    };
</script>
<div>
    {#if $mutation.isLoading}
        <p>...loading</p>
    <!-- {:else if $mutation.isError}
        <p>Error : {$mutation.error.message}</p> -->
    {:else if $mutation.isSuccess}
        <p>Todo added success</p>
    {:else}
        <form on:submit|preventDefault={onSubmit}>
            <input bind:value={title} type="text" />
            <button>Click</button>
        </form>
    {/if}
</div>