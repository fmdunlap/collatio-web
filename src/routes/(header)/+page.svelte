<script lang="ts">
	import { goto } from '$app/navigation';
	import Chevron from '../../assets/Chevron.svelte';
</script>

<!-- Collatio Header -->
<div class="h-screen w-screen bg-black">
	<div class="mx-auto w-fit h-full flex flex-col">
		<div class="flex flex-row items-stretch mt-40">
			<p class="text-6xl font-sans text-white">Collatio</p>
			<p class="pl-2 text-white mt-auto align-middle font-light text-2xl font-mono">(noun)</p>
		</div>
		<p class="text-white font-light text-xl font-sans">Col·la·tio | \kolˈlaː.ti.oː\</p>
		<ol class="mt-6 text-white font-mono font-light list-inside text-sm">
			<li>1. Collecting (bringing together)</li>
			<li>2. Union, combination</li>
			<li>3. Comparison, collation (of facts)</li>
		</ol>
		<div class="flex-grow">
			<!-- svelte-ignore a11y-no-noninteractive-element-interactions -->
			<!-- svelte-ignore a11y-click-events-have-key-events -->
			<p
				class="select-none mx-auto my-auto"
				on:click={() => {
					goto('/redirect/');
				}}
			>
				You Found Me!
			</p>
		</div>
		<Chevron class="mx-auto bottom-4" />
	</div>
</div>