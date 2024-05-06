<template>
	<div class="flex flex-col gap-3">
		<h1 class="text-2xl font-bold">{{ title }}</h1>
		<p class="text-sm text-gray-500 mb-2">{{ description }}</p>
	</div>
</template>

<script setup>
defineProps({
  title: String,
  description: String
})
</script>
