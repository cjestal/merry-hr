<template>
	<div class="hidden xl:fixed xl:inset-y-0 xl:z-50 xl:flex xl:w-72 xl:flex-col bg-gray-600">
		<!-- Sidebar component, swap this element with another sidebar if you like -->
		<div
			class="flex grow flex-col gap-y-5 overflow-y-auto bg-black/10 px-6 ring-1 ring-white/5"
		>
			<div class="flex h-16 shrink-0 items-center">
				<img
					class="h-8 w-auto"
					src="https://tailwindui.com/img/logos/mark.svg?color=yellow&shade=500"
					alt="Your Company"
				/>
			</div>
			<nav class="flex flex-1 flex-col">
				<ul role="list" class="flex flex-1 flex-col gap-y-7">
					<li>
						<ul role="list" class="-mx-2 space-y-1">
							<li v-for="item in navigation" :key="item.name">
								<a
									:href="item.href"
									:class="[
										item.current
											? 'bg-yellow-600 text-white'
											: 'text-gray-50 hover:text-white hover:bg-gray-700',
										'group flex gap-x-3 rounded-md p-2 text-sm leading-6 font-semibold',
									]"
								>
									<component
										:is="item.icon"
										class="h-6 w-6 shrink-0"
										aria-hidden="true"
									/>
									{{ item.name }}
								</a>
							</li>
						</ul>
					</li>
					<li>
						<div class="text-xs font-semibold leading-6 text-gray-400">
							Your teams
						</div>
						<ul role="list" class="-mx-2 mt-2 space-y-1">
							<li v-for="team in teams" :key="team.name">
								<a
									:href="team.href"
									:class="[
										team.current
											? 'bg-gray-700 text-white'
											: 'text-gray-400 hover:text-white hover:bg-gray-700',
										'group flex gap-x-3 rounded-md p-2 text-sm leading-6 font-semibold',
									]"
								>
									<span
										class="flex h-6 w-6 shrink-0 items-center justify-center rounded-lg border border-gray-700 bg-gray-700 text-[0.625rem] font-medium text-gray-400 group-hover:text-white"
										>{{ team.initial }}</span
									>
									<span class="truncate">{{ team.name }}</span>
								</a>
							</li>
						</ul>
					</li>
					<li class="-mx-6 mt-auto">
						<a
							href="#"
							class="flex items-center gap-x-4 px-6 py-3 text-sm font-semibold leading-6 text-white hover:bg-gray-700"
						>
							<img
								class="h-8 w-8 rounded-full bg-gray-700"
								src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
								alt=""
							/>
							<span class="sr-only">Your profile</span>
							<span aria-hidden="true">Tom Cook</span>
						</a>
					</li>
				</ul>
			</nav>
		</div>
	</div>
</template>

<script setup>
import {
	ChartBarSquareIcon,
	Cog6ToothIcon,
	FolderIcon,
	GlobeAltIcon,
	ServerIcon,
	SignalIcon,
	XMarkIcon,
} from "@heroicons/vue/24/outline";

const navigation = [
	{ name: "Projects", href: "#", icon: FolderIcon, current: false },
	{ name: "Deployments", href: "#", icon: ServerIcon, current: true },
	{ name: "Activity", href: "#", icon: SignalIcon, current: false },
	{ name: "Domains", href: "#", icon: GlobeAltIcon, current: false },
	{ name: "Usage", href: "#", icon: ChartBarSquareIcon, current: false },
	{ name: "Settings", href: "#", icon: Cog6ToothIcon, current: false },
];
</script>
