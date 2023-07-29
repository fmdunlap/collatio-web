<script lang="ts">
	import type { Avatar } from '../types/avatar';

	export let avatar: Avatar;
</script>

<div class="flex flex-col px-8">
	<img
		class="rounded-full w-4/5 h-4/5 self-center md:h-64 md:w-64"
		src={avatar.imageSrc}
		alt={avatar.imageAlt}
	/>
	<p class="text-white text-4xl font-sans text-center font-light my-4">{avatar.name}</p>
</div>
