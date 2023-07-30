<script lang="ts">
	import { projectsScrollPoint, comradesScrollPoint } from '../stores/HeaderScrollPointStore';
	import TooltipButton from './TooltipButton.svelte';
	import { CONTACT_EMAIL } from '../data/contact';

	function scrollToPoint(point: number) {
		scrollTo({ top: point, behavior: 'smooth' });
	}
</script>

<header class="max-w-screen fixed z-10 flex w-screen flex-row bg-black">
	<div class="my-2 flex flex-grow justify-around md:ml-8 md:justify-start md:gap-x-12">
		<button
			class="font-sans text-lg text-white hover:cursor-pointer hover:underline"
			on:click={() => {
				scrollToPoint($projectsScrollPoint);
			}}
		>
			Projects
		</button>
		<button
			class="font-sans text-lg text-white hover:cursor-pointer hover:underline"
			on:click={() => {
				scrollToPoint($comradesScrollPoint);
			}}>Comrades</button
		>
		<TooltipButton
			buttonText="Contact"
			tooltipText="Copied {CONTACT_EMAIL}"
			onClickAction={() => {
				navigator.clipboard.writeText(CONTACT_EMAIL);
			}}
		/>
	</div>
</header>
