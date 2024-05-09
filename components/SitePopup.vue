<template>
	<div
		v-if="isVisible"
		class="pointer-events-none fixed inset-x-0 bottom-0 px-6 pb-6"
	>
		<div
			class="pointer-events-auto ml-auto max-w-xl rounded-xl bg-white p-6 shadow-lg ring-1 ring-gray-900/10"
		>
			<p class="text-sm leading-6 text-gray-900 z-0">
				Thanks for visiting <span class="font-semibold">Merry HR</span>. This is a work in progress and will be
				updated with more features soon. I'm looking forward to adding more
				content and improving the user experience. - <i class="font-semibold text-red-700">Clint James</i>
			</p>
			
			<div class="mt-4 flex items-center gap-x-5">
				<button
					type="button"
					class="rounded-md bg-yellow-500 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-gray-700 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-gray-900"
					@click="isVisible = false"
				>
					Understood
				</button>
				<!-- <button
					type="button"
					class="text-sm font-semibold leading-6 text-gray-900"
				>
					Reject all
				</button> -->
			</div>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			isVisible: true,
		};
	},
};
</script>
