<template>
	<html class="h-full bg-gray-50">
		<body class="h-full">
			<div class="h-full bg-gray-50">
				<SiteNavMobile /> <!-- Mobile navigation -->
				<SiteNav /> <!-- Desktop navigation -->

				<div class="xl:pl-72">
					<!-- Sticky search header -->
					<div
						class="sticky top-0 z-40 flex h-16 shrink-0 items-center gap-x-6 border-b  px-4 shadow-sm sm:px-6 lg:px-8"
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
										class="pointer-events-none absolute inset-y-0 left-0 h-full w-5 text-gray-500"
										aria-hidden="true"
									/>
									<input
										id="search-field"
										class="block h-full w-full border-0 bg-transparent py-0 pl-8 pr-0 text-white focus:ring-0 sm:text-sm"
										placeholder="Search..."
										type="search"
										name="search"
									/>
								</div>
							</form>
						</div>
					</div>

					<SitePage />
				</div>
			</div>
		</body>
	</html>
</template>

<script setup>
import { ref } from "vue";

import {
	Bars3Icon,
	MagnifyingGlassIcon,
} from "@heroicons/vue/20/solid";

const teams = [
	{ id: 1, name: "Planetaria", href: "#", initial: "P", current: false },
	{ id: 2, name: "Protocol", href: "#", initial: "P", current: false },
	{ id: 3, name: "Tailwind Labs", href: "#", initial: "T", current: false },
];
const statuses = {
	offline: "text-gray-500 bg-gray-100/10",
	online: "text-green-400 bg-green-400/10",
	error: "text-rose-400 bg-rose-400/10",
};
const environments = {
	Preview: "text-gray-400 bg-gray-400/10 ring-gray-400/20",
	Production: "text-indigo-400 bg-indigo-400/10 ring-indigo-400/30",
};
const deployments = [
	{
		id: 1,
		href: "#",
		projectName: "ios-app",
		teamName: "Planetaria",
		status: "offline",
		statusText: "Initiated 1m 32s ago",
		description: "Deploys from GitHub",
		environment: "Preview",
	},
	// More deployments...
];
const activityItems = [
	{
		user: {
			name: "Michael Foster",
			imageUrl:
				"https://images.unsplash.com/photo-1519244703995-f4e0f30006d5?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
		},
		projectName: "ios-app",
		commit: "2d89f0c8",
		branch: "main",
		date: "1h",
		dateTime: "2023-01-23T11:00",
	},
];

const sidebarOpen = ref(false);
</script>
