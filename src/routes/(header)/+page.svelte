<script lang="ts">
	import Chevron from '../../assets/Chevron.svelte';
	import Avatar from '../../component/Avatar.svelte';
	import ProjectCard from '../../component/ProjectCard.svelte';
	import { onMount } from 'svelte';
	import { fly } from 'svelte/transition';
	import { cubicIn } from 'svelte/easing';

	const BOTTOM_BAR_EXTENSION_FACTOR = 1.15;
	const BOTTOM_BAR_JOKE_TEXT = [
		"Congratulations! You've reached the elusive footer bar. Take a moment to celebrate this small victory.",
		"Are you lost? Don't worry, you're not alone. Very few adventurers make it down here.",
		"Hidden treasure lies in the footer of this website. You're one of the lucky few who discovered it.",
		"This is the footer - where unicorns dance and dreams come true. You're officially part of the magic.",
		'Feeling accomplished? You made it to the bottom. Now go back to the top and start all over again.',
		'Welcome to the Footer, a mythical land of secrets and surprises. Have you brought your sense of adventure?',
		"If you're reading this, you deserve a gold star for scrolling skills. Well done!",
		'Footer bar: where legends are made. Consider yourself an explorer of the deepest corners of the website.',
		'The bottom of the page is a lonely place. Thanks for keeping me company down here!',
		'Warning: Scrolling to the bottom may cause a sense of achievement and an overwhelming desire to share this accomplishment.'
	];
	let windowHeight: number;
	let bottomBar: HTMLDivElement;
	let bottomBarThreshold: number = 0;
	let yScrollPoint: number = 0;
	$: showBottomBar = true;

	function onScroll() {
		if (yScrollPoint > bottomBarThreshold) {
			showBottomBar = true;
		} else {
			showBottomBar = false;
		}
	}

	let bottomBarBeingMeasured = false;
	function setBottomBarThreshold() {
		if (!bottomBarBeingMeasured) {
			bottomBarBeingMeasured = true;
			showBottomBar = true;
			let bottomBarInterval = setInterval(() => {
				let bodyHeight: number = document.body.scrollHeight;
				let bottomBarHeight = bottomBar.clientHeight;
				bottomBarThreshold =
					bodyHeight - windowHeight - BOTTOM_BAR_EXTENSION_FACTOR * bottomBarHeight;
				showBottomBar = false;
				clearInterval(bottomBarInterval);
				bottomBarBeingMeasured = false;
			}, 50);
		}
	}

	onMount(() => {
		setBottomBarThreshold();
	});
</script>

<svelte:window
	bind:scrollY={yScrollPoint}
	on:scroll={onScroll}
	bind:innerHeight={windowHeight}
	on:resize={setBottomBarThreshold}
/>

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
<!-- Projects -->
<div class="flex flex-col mx-4 mt-10 pb-4 gap-6">
	<ProjectCard
		title="Project #1"
		imageAlt="A ktten"
		imageSrc="https://placekitten.com/400/250"
		description="Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur."
	/>
	<ProjectCard
		title="Project #2"
		imageAlt="A ktten"
		imageSrc="https://placekitten.com/400/251"
		description="Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur."
	/>
	<ProjectCard
		title="Project #3"
		imageAlt="A ktten"
		imageSrc="https://placekitten.com/400/252"
		description="Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur."
	/>
	<ProjectCard
		title="Project #4"
		imageAlt="A ktten"
		imageSrc="https://placekitten.com/400/253"
		description="Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur."
	/>
</div>
<!-- Avatar -->
<div class="mx-10 mt-10 pb-3">
	<Avatar imageSrc="https://placekitten.com/200/200" imageAlt="A kitten" name="Kitten" />
	<Avatar imageSrc="https://placekitten.com/201/200" imageAlt="A kitten" name="Kitten" />
	<Avatar imageSrc="https://placekitten.com/202/202" imageAlt="A kitten" name="Kitten" />
	<Avatar imageSrc="https://placekitten.com/203/200" imageAlt="A kitten" name="Kitten" />
</div>
<!-- Bottom Bar Gag -->
{#if showBottomBar}
	<div class="relative bg-black overflow-clip" bind:this={bottomBar}>
		<p
			transition:fly={{ y: 100, easing: cubicIn }}
			class="text-white mx-8 pb-4 text-center text-sm text-mono"
		>
			{BOTTOM_BAR_JOKE_TEXT[Math.floor(Math.random() * BOTTOM_BAR_JOKE_TEXT.length)]}
		</p>
	</div>
{/if}
