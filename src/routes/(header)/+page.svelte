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
		projectsScrollPoint.set(projectsDiv.offsetTop - 50 || 0);
		comradesScrollPoint.set(comradesDiv.offsetTop - 50 || 0);
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

<svelte:window bind:scrollY={yScrollPoint} on:scroll={onScroll} on:resize={setBottomBarThreshold} />

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
<div bind:this={projectsDiv} class="flex flex-col mx-4 mt-10 pb-4 gap-6">
	{#each PROJECTS as project}
		<ProjectCard {project} />
	{/each}
</div>
<!-- Avatar -->
<div bind:this={comradesDiv} class="mx-10 mt-10 pb-3">
	{#each AVATARS as avatar}
		<AvatarView {avatar} />
	{/each}
</div>
<!-- Bottom Bar Gag -->
<div class="relative h-20 bg-black overflow-clip" bind:this={bottomBar}>
	{#if showBottomBarText}
		<p
			transition:fly={{ y: 100, easing: cubicIn }}
			class="text-white mx-8 pb-4 text-center text-sm text-mono"
		>
			{BOTTOM_BAR_JOKE_TEXT[Math.floor(Math.random() * BOTTOM_BAR_JOKE_TEXT.length)]}
		</p>
	{/if}
</div>
