<script lang="ts">
	import type { Project } from '../data/project';

	export let project: Project;
</script>

<div class="flex grow flex-col justify-self-stretch border-x border-y border-solid border-gray-500">
	<h1 class="mx-auto my-4 text-white text-4xl font-sans">{project.title}</h1>
	<hr class="mx-4 border-px border-solid border-gray-500" />
	<img class="my-4 mx-10" src={project.imageSrc} alt={project.imageAlt} />
	<p class="text-white font-mono my-4 mx-8 text-sm">
		{project.description}
	</p>
	<div class="text-end p-4">
		<a class="text-white text-lg underline hover:text-gray-300" href={project.projectUrl}
			>See More -&gt;</a
		>
	</div>
</div>
