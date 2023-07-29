<script lang="ts">
	import { projectsScrollPoint, comradesScrollPoint } from '../stores/HeaderScrollPointStore';

	function scrollToPoint(point: number) {
		scrollTo({ top: point, behavior: 'smooth' });
	}
</script>

<header class="max-w-screen fixed flex w-screen flex-row bg-black z-10">
	<div class="my-2 flex flex-grow justify-around md:ml-4 md:justify-start md:gap-x-12">
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
		<button class="font-sans text-lg text-white hover:cursor-pointer hover:underline"
			>Contact</button
		>
	</div>
</header>
