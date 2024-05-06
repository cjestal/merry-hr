<template>
	<div class="md:flex md:items-center md:justify-between">
		<div class="flex flex-col gap-3">
			<BreadCrumbs />
			<h1 class="text-2xl font-bold">{{ title }}</h1>
			<p class="text-sm text-gray-500 mb-2">{{ description }}</p>
		</div>
		<div class="flex gap-3">
			<slot />
		</div>
	</div>
</template>

<script setup>
defineProps({
	title: String,
	description: String,
});
</script>
