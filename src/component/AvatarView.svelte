<script lang="ts">
	import type { Avatar } from '../data/avatar';

	export let avatar: Avatar;
</script>

<div class="flex flex-col px-8">
	<img
		class="h-4/5 w-4/5 self-center rounded-full md:h-64 md:w-64"
		src={avatar.imageSrc}
		alt={avatar.imageAlt}
	/>
	<p class="my-4 text-center font-sans text-4xl font-light text-white">{avatar.name}</p>
</div>
