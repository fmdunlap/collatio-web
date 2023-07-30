<script lang="ts">
	import Chevron from '../../assets/Chevron.svelte';
	import AvatarView from '../../component/AvatarView.svelte';
	import ProjectCard from '../../component/ProjectCard.svelte';
	import { onMount } from 'svelte';
	import { fly } from 'svelte/transition';
	import { cubicIn } from 'svelte/easing';
	import { projectsScrollPoint, comradesScrollPoint } from '../../stores/HeaderScrollPointStore';
	import type { Avatar } from '../../types/avatar';
	import type { Project } from '../../types/project';

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

	const AVATARS: Avatar[] = [
		{
			name: 'Kitten',
			imageSrc: 'https://placekitten.com/200/200',
			imageAlt: 'A kitten'
		},
		{
			name: 'Kitten',
			imageSrc: 'https://placekitten.com/201/200',
			imageAlt: 'A kitten'
		},
		{
			name: 'Kitten',
			imageSrc: 'https://placekitten.com/202/202',
			imageAlt: 'A kitten'
		},
		{
			name: 'Kitten',
			imageSrc: 'https://placekitten.com/203/200',
			imageAlt: 'A kitten'
		}
	];

	const PROJECTS: Project[] = [
		{
			title: 'Project #1',
			imageSrc: 'https://placekitten.com/400/250',
			imageAlt: 'A kitten',
			description:
				'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'
		},
		{
			title: 'Project #2',
			imageSrc: 'https://placekitten.com/400/251',
			imageAlt: 'A kitten',
			description:
				'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'
		},
		{
			title: 'Project #3',
			imageSrc: 'https://placekitten.com/400/252',
			imageAlt: 'A kitten',
			description:
				'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'
		},
		{
			title: 'Project #4',
			imageSrc: 'https://placekitten.com/400/253',
			imageAlt: 'A kitten',
			description:
				'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'
		}
	];

	let bottomBar: HTMLDivElement;
	let bottomBarThreshold: number = 0;
	let yScrollPoint: number = 0;
	let projectsDiv: HTMLDivElement;
	let comradesDiv: HTMLDivElement;

	$: showBottomBarText = true;

	function setHeaderScrollPoints() {
		console.log();
		projectsScrollPoint.set(projectsDiv.offsetTop - 70 || 0);
		comradesScrollPoint.set(comradesDiv.offsetTop - 70 || 0);
	}

	function onScroll() {
		if (yScrollPoint > bottomBarThreshold) {
			showBottomBarText = true;
		} else {
			showBottomBarText = false;
		}
	}

	function setBottomBarThreshold() {
		bottomBarThreshold =
			document.body.scrollHeight -
			window.innerHeight -
			BOTTOM_BAR_EXTENSION_FACTOR * bottomBar.clientHeight;
	}

	onMount(() => {
		setBottomBarThreshold();
		setHeaderScrollPoints();
	});
</script>

<svelte:window
	bind:scrollY={yScrollPoint}
	on:scroll={onScroll}
	on:resize={() => {
		setBottomBarThreshold();
		setHeaderScrollPoints();
	}}
/>

<!-- Collatio Hero -->
<div class="flex h-screen min-h-screen w-screen flex-col">
	<div class="m-auto flex max-w-screen-2xl flex-row lg:w-2/3">
		<div class="m-auto flex flex-col">
			<div class="mt-40 flex flex-row items-stretch md:mt-0">
				<p class="font-sans text-6xl text-white md:text-8xl">Collatio</p>
				<p
					class="mt-auto pb-3 pl-2 align-middle font-mono text-2xl font-light text-white md:text-4xl"
				>
					(noun)
				</p>
			</div>
			<p class="font-sans text-xl font-light text-white md:ml-2 md:text-2xl">
				Col·la·tio | \kol`la:.ti.o:\
			</p>
			<ol class="mt-6 list-inside font-mono text-sm font-light text-white md:text-lg">
				<li>1. Collecting (bringing together)</li>
				<li>2. Union, combination</li>
				<li>3. Comparison, collation (of facts)</li>
			</ol>
		</div>
		<div class="mx-8 my-auto hidden h-96 w-px min-w-fit bg-zinc-600 lg:block" />
		<p
			class="text-md m-auto hidden max-h-96 overflow-scroll pl-16 align-middle font-mono text-white lg:block"
		>
			Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut
			labore et dolore magna aliqua. Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
			eiusmod tempor incididunt ut labore et dolore magna aliqua. Lorem ipsum dolor sit amet,
			consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna
			aliqua.
		</p>
	</div>
	<span class="grow lg:hidden" />
	<div class="bottom-10 mx-auto w-fit lg:hidden">
		<Chevron />
	</div>
</div>
<!-- Projects -->
<h1
	bind:this={projectsDiv}
	class="my-14 text-center font-sans text-5xl text-white md:mx-auto md:max-w-screen-2xl md:text-start"
>
	Our Projects
</h1>
<div class="mx-4 mt-10 flex flex-col gap-6 pb-4 md:mx-auto md:max-w-screen-2xl md:flex-row">
	{#each PROJECTS as project}
		<ProjectCard {project} />
	{/each}
</div>
<!-- Avatar -->
<h1
	bind:this={comradesDiv}
	class="my-14 text-center font-sans text-5xl text-white md:mx-auto md:max-w-screen-2xl md:text-start"
>
	The Comrades
</h1>
<div
	class="mx-10 mt-10 flex flex-col pb-3 md:mx-auto md:max-w-screen-2xl md:flex-row md:justify-around"
>
	{#each AVATARS as avatar}
		<AvatarView {avatar} />
	{/each}
</div>
<!-- Bottom Bar Gag -->
<div class="relative h-20 overflow-clip bg-black md:h-12" bind:this={bottomBar}>
	{#if showBottomBarText}
		<p
			transition:fly={{ y: 100, easing: cubicIn }}
			class="text-mono mx-8 pb-4 text-center text-sm text-white"
		>
			{BOTTOM_BAR_JOKE_TEXT[Math.floor(Math.random() * BOTTOM_BAR_JOKE_TEXT.length)]}
		</p>
	{/if}
</div>
