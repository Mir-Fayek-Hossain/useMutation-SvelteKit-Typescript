<script>
    import { useQuery } from '@sveltestack/svelte-query'
     const queryResult = useQuery('repoData', () => {
      return fetch(
        'https://api.github.com/repos/SvelteStack/svelte-query'
      ).then(res => res.json())
    })
  </script>
    {#if $queryResult.isLoading}
    Loading...
  {:else if $queryResult.error}
    An error has occurred:
  {:else}
    <div>
      <h1>{$queryResult.data.name}</h1>
      <p>{$queryResult.data.description}</p>
      <strong>:eyes: {$queryResult.data.subscribers_count}</strong>{' '}
      <strong>:sparkles: {$queryResult.data.stargazers_count}</strong>{' '}
      <strong>:fork_and_knife: {$queryResult.data.forks_count}</strong>
    </div>
  {/if}