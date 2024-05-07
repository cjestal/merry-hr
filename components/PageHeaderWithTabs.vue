<template>
	<div class="relative border-b border-gray-200 pb-5 sm:pb-0">
		<div class="md:flex md:items-center md:justify-between">
			<div class="flex flex-col gap-3">
				<BreadCrumbs />
				<h1 class="text-2xl font-bold">{{ title }}</h1>
				<p class="text-sm text-gray-500 mb-2">{{ description }}</p>
			</div>
			<div class="mt-3 flex md:absolute md:right-0 md:top-3 md:mt-0">
				<!-- <button
					type="button"
					class="inline-flex items-center rounded-md bg-white px-3 py-2 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 hover:bg-gray-50"
				>
					Share
				</button> -->
				<button
					type="button"
					class="ml-3 inline-flex items-center rounded-md bg-yellow-500 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-yellow-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-yellow-600"
				>
					Create
				</button>
			</div>
		</div>
		<div class="mt-4">
			<div class="sm:hidden">
				<label for="current-tab" class="sr-only">Select a tab</label>
				<select
					id="current-tab"
					name="current-tab"
					class="block w-full rounded-md border-0 py-1.5 pl-3 pr-10 ring-1 ring-inset ring-gray-300 focus:ring-2 focus:ring-inset focus:ring-yellow-600"
				>
					<option v-for="tab in tabs" :key="tab.name" :selected="tab.href === $route.path">
						{{ tab.name }}
					</option>
				</select>
			</div>
			<div class="hidden sm:block">
				<nav class="-mb-px flex space-x-8">
					<NuxtLink
						v-for="tab in tabs"
						:key="tab.name"
						:href="tab.href"
						:class="[
							tab.href === $route.path
								? 'border-yellow-500 text-yellow-600'
								: 'border-transparent text-gray-500 hover:border-gray-300 hover:text-gray-700',
							'whitespace-nowrap border-b-2 px-1 pb-4 text-sm font-medium',
						]"
						:aria-current="tab.href === $route.path ? 'page' : undefined"
						>{{ tab.name }}</NuxtLink
					>
				</nav>
			</div>
		</div>
	</div>
</template>

<script setup>
import { useRoute } from 'vue-router';
const { title, description, tabs } = defineProps({
	title: String,
	description: String,
	tabs: Array,
});
const $route = useRoute();
</script>
