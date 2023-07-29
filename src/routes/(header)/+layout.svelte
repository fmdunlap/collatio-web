<script>
	import Header from '../../component/Header.svelte';

	export let headerObject;
</script>

<Header bind:this={headerObject} />
<slot />
