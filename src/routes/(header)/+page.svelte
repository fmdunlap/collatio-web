<script lang="ts">
	import Chevron from '../../assets/Chevron.svelte';
	import ProjectCard from '../../component/ProjectCard.svelte';
</script>

<!-- Collatio Header -->
<div class="mx-auto flex h-screen min-h-screen w-fit flex-col">
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
	<span class="grow" />
	<div class="bottom-10 mx-auto w-fit">
		<Chevron />
	</div>
</div>
<div class="mx-4 mt-10 pb-4">
	<ProjectCard
		title="Project #1"
		imageAlt="A ktten"
		imageSrc="https://placekitten.com/400/250"
		description="Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur."
	/>
</div>
