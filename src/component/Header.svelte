<script lang="ts">
	import { projectsScrollPoint, comradesScrollPoint } from '../stores/HeaderScrollPointStore';

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
		<a
			class="font-sans text-lg text-white hover:cursor-pointer hover:underline"
			href="mailto:email@example.com">Contact</a
		>
	</div>
</header>
