<script lang="ts">
	import { goto } from '$app/navigation';
	import Chevron from '../../assets/Chevron.svelte';
</script>

<!-- Collatio Header -->
<div class="h-screen w-screen bg-black">
	<div class="mx-auto flex h-full w-fit flex-col">
		<div class="mt-40 flex flex-row items-stretch">
			<p class="font-sans text-6xl text-white">Collatio</p>
			<p class="mt-auto pl-2 align-middle font-mono text-2xl font-light text-white">(noun)</p>
		</div>
		<p class="font-sans text-xl font-light text-white">Col·la·tio | \kolˈlaː.ti.oː\</p>
		<ol class="mt-6 list-inside font-mono text-sm font-light text-white">
			<li>1. Collecting (bringing together)</li>
			<li>2. Union, combination</li>
			<li>3. Comparison, collation (of facts)</li>
		</ol>
		<div class="flex-grow">
			<!-- svelte-ignore a11y-no-noninteractive-element-interactions -->
			<!-- svelte-ignore a11y-click-events-have-key-events -->
			<p
				class="mx-auto my-auto select-none"
				on:click={() => {
					goto('/redirect/');
				}}
			>
				You Found Me!
			</p>
		</div>
		<Chevron class="bottom-4 mx-auto" />
	</div>
</div>
