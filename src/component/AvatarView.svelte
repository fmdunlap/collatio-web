<script lang="ts">
	import type { Avatar } from '../types/avatar';

	export let avatar: Avatar;
</script>

<div class="flex flex-col">
	<img class="rounded-full w-4/5 h-4/5 self-center" src={avatar.imageSrc} alt={avatar.imageAlt} />
	<p class="text-white text-4xl font-sans text-center font-light my-4">{avatar.name}</p>
</div>
