<script lang="ts">
	import { fade } from 'svelte/transition';

	export let buttonText: string;
	export let tooltipText: string;
	export let tooltipDuration: number = 2000;
	export let onClickAction = () => {};

	let button: HTMLDivElement;
	let tooltip: HTMLDivElement;

	let tooltipShown = false;

	function setTooltipBounds() {
		let buttonBounds = button.getBoundingClientRect();
		let tooltipBounds = tooltip.getBoundingClientRect();

		let tooltipLeftOffset = buttonBounds.width / 2 - tooltipBounds.width / 2;

		if (tooltipBounds.left + tooltipLeftOffset + tooltipBounds.width > window.innerWidth) {
			tooltipLeftOffset = -tooltipBounds.width + buttonBounds.width;
		} else if (tooltipBounds.left + tooltipLeftOffset < 0) {
			tooltipLeftOffset = 0;
		}

		tooltip.style.left = `${tooltipLeftOffset}px`;
	}
</script>

<div class="relative">
	<!-- svelte-ignore a11y-no-static-element-interactions -->
	<!-- svelte-ignore a11y-click-events-have-key-events -->
	<div
		bind:this={button}
		on:click={() => {
			tooltipShown = true;
			onClickAction();
			setTimeout(() => {
				tooltipShown = false;
			}, tooltipDuration);
		}}
	>
		<slot name="button">
			<button class="font-sans text-lg text-white hover:cursor-pointer hover:underline">
				{buttonText}
			</button>
		</slot>
	</div>
	{#if tooltipShown}
		<div
			bind:this={tooltip}
			class="absolute top-10 rounded-md bg-zinc-700"
			transition:fade={{ duration: tooltipDuration / 10 }}
			on:introstart={setTooltipBounds}
		>
			<slot name="tooltip">
				<p class="m-4 text-center text-white">
					{tooltipText}
				</p>
			</slot>
		</div>
	{/if}
</div>
