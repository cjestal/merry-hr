<template>
	<html class="h-full bg-gray-50">
		<body class="h-full">
			<div class="h-full bg-gray-50">
				<!-- <SiteNavMobile /> Mobile navigation -->
				<SiteNav />
				<!-- Desktop navigation -->

				<div class="xl:pl-72">
					<SiteAnnouncement />
					<!-- <SitePopup /> -->
					<div
						class="sticky top-0 z-40 flex h-16 shrink-0 items-center gap-x-6 border-b px-4 shadow-sm sm:px-6 lg:px-8 bg-gray-50"
					>
						<button
							type="button"
							class="-m-2.5 p-2.5 text-white xl:hidden"
							@click="sidebarOpen = true"
						>
							<span class="sr-only">Open sidebar</span>
							<Bars3Icon class="h-5 w-5" aria-hidden="true" />
						</button>

						<div class="flex flex-1 gap-x-4 self-stretch lg:gap-x-6">
							<form class="flex flex-1" action="#" method="GET">
								<label for="search-field" class="sr-only">Search</label>
								<div class="relative w-full">
									<MagnifyingGlassIcon
										class="pointer-events-none absolute inset-y-0 left-0 h-full w-5 text-gray-900"
										aria-hidden="true"
									/>
									<input
										id="search-field"
										class="block h-full w-full border-0 bg-transparent py-0 pl-8 pr-0 text-gray-900 focus:ring-0 sm:text-sm outline-none"
										placeholder="Search..."
										type="search"
										name="search"
									/>
								</div>
							</form>
						</div>
					</div>
					<NuxtPage />
				</div>
			</div>
		</body>
	</html>
</template>

<script setup>
import { ref } from "vue";

import { Bars3Icon, MagnifyingGlassIcon } from "@heroicons/vue/20/solid";

const sidebarOpen = ref(false);
</script>
