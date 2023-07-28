<script lang="ts">
	export let name: string;
	export let imageSrc: string;
	export let imageAlt: string;
</script>

<div class="flex flex-col">
	<img class="rounded-full w-4/5 h-4/5 self-center" src={imageSrc} alt={imageAlt} />
	<p class="text-white text-4xl font-sans text-center font-light my-4">{name}</p>
</div>
