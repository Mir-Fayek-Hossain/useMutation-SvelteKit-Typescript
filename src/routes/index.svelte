<script>
	import Test from '../components/Test.svelte';

	import { QueryClient, QueryClientProvider } from '@sveltestack/svelte-query';

	const qC = new QueryClient();
</script>

helloos

<QueryClientProvider client={qC}>
	<Test />
</QueryClientProvider>
