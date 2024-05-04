<template>
	<main class="">
		<header
			class="flex items-center justify-between border-b border-white/5 px-4 py-4 sm:px-6 sm:py-6 lg:px-8"
		>
			<h1 class="text-base font-semibold leading-7 text-white">Deployments</h1>

			<!-- Sort dropdown -->
			<Menu as="div" class="relative">
				<MenuButton
					class="flex items-center gap-x-1 text-sm font-medium leading-6 text-white"
				>
					Sort by
					<ChevronUpDownIcon class="h-5 w-5 text-gray-500" aria-hidden="true" />
				</MenuButton>
				<transition
					enter-active-class="transition ease-out duration-100"
					enter-from-class="transform opacity-0 scale-95"
					enter-to-class="transform opacity-100 scale-100"
					leave-active-class="transition ease-in duration-75"
					leave-from-class="transform opacity-100 scale-100"
					leave-to-class="transform opacity-0 scale-95"
				>
					<MenuItems
						class="absolute right-0 z-10 mt-2.5 w-40 origin-top-right rounded-md bg-white py-2 shadow-lg ring-1 ring-gray-900/5 focus:outline-none"
					>
						<MenuItem v-slot="{ active }">
							<a
								href="#"
								:class="[
									active ? 'bg-gray-50' : '',
									'block px-3 py-1 text-sm leading-6 text-gray-900',
								]"
								>Name</a
							>
						</MenuItem>
						<MenuItem v-slot="{ active }">
							<a
								href="#"
								:class="[
									active ? 'bg-gray-50' : '',
									'block px-3 py-1 text-sm leading-6 text-gray-900',
								]"
								>Date updated</a
							>
						</MenuItem>
						<MenuItem v-slot="{ active }">
							<a
								href="#"
								:class="[
									active ? 'bg-gray-50' : '',
									'block px-3 py-1 text-sm leading-6 text-gray-900',
								]"
								>Environment</a
							>
						</MenuItem>
					</MenuItems>
				</transition>
			</Menu>
		</header>

		<!-- Deployment list -->
		<ul role="list" class="divide-y divide-white/5">
			<li
				v-for="deployment in deployments"
				:key="deployment.id"
				class="relative flex items-center space-x-4 px-4 py-4 sm:px-6 lg:px-8"
			>
				<div class="min-w-0 flex-auto">
					<div class="flex items-center gap-x-3">
						<div
							:class="[
								statuses[deployment.status],
								'flex-none rounded-full p-1',
							]"
						>
							<div class="h-2 w-2 rounded-full bg-current" />
						</div>
						<h2 class="min-w-0 text-sm font-semibold leading-6 text-white">
							<a :href="deployment.href" class="flex gap-x-2">
								<span class="truncate">{{ deployment.teamName }}</span>
								<span class="text-gray-400">/</span>
								<span class="whitespace-nowrap">{{
									deployment.projectName
								}}</span>
								<span class="absolute inset-0" />
							</a>
						</h2>
					</div>
					<div
						class="mt-3 flex items-center gap-x-2.5 text-xs leading-5 text-gray-400"
					>
						<p class="truncate">{{ deployment.description }}</p>
						<svg viewBox="0 0 2 2" class="h-0.5 w-0.5 flex-none fill-gray-300">
							<circle cx="1" cy="1" r="1" />
						</svg>
						<p class="whitespace-nowrap">{{ deployment.statusText }}</p>
					</div>
				</div>
				<div
					:class="[
						environments[deployment.environment],
						'rounded-full flex-none py-1 px-2 text-xs font-medium ring-1 ring-inset',
					]"
				>
					{{ deployment.environment }}
				</div>
				<ChevronRightIcon
					class="h-5 w-5 flex-none text-gray-400"
					aria-hidden="true"
				/>
			</li>
		</ul>
	</main>
</template>

<script setup>
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
	// More items...
];
</script>
