<template>
	<TransitionRoot as="template" :show="sidebarOpen">
		<Dialog class="relative z-50 xl:hidden" @close="sidebarOpen = false">
			<TransitionChild
				as="template"
				enter="transition-opacity ease-linear duration-300"
				enter-from="opacity-0"
				enter-to="opacity-100"
				leave="transition-opacity ease-linear duration-300"
				leave-from="opacity-100"
				leave-to="opacity-0"
			>
				<div class="fixed inset-0 bg-gray-900/80" />
			</TransitionChild>

			<div class="fixed inset-0 flex">
				<TransitionChild
					as="template"
					enter="transition ease-in-out duration-300 transform"
					enter-from="-translate-x-full"
					enter-to="translate-x-0"
					leave="transition ease-in-out duration-300 transform"
					leave-from="translate-x-0"
					leave-to="-translate-x-full"
				>
					<DialogPanel class="relative mr-16 flex w-full max-w-xs flex-1">
						<TransitionChild
							as="template"
							enter="ease-in-out duration-300"
							enter-from="opacity-0"
							enter-to="opacity-100"
							leave="ease-in-out duration-300"
							leave-from="opacity-100"
							leave-to="opacity-0"
						>
							<div
								class="absolute left-full top-0 flex w-16 justify-center pt-5"
							>
								<button
									type="button"
									class="-m-2.5 p-2.5"
									@click="sidebarOpen = false"
								>
									<span class="sr-only">Close sidebar</span>
									<XMarkIcon class="h-6 w-6 text-white" aria-hidden="true" />
								</button>
							</div>
						</TransitionChild>
						<!-- Sidebar component, swap this element with another sidebar if you like -->
						<div
							class="flex grow flex-col gap-y-5 overflow-y-auto bg-gray-900 px-6 ring-1 ring-white/10"
						>
							<div class="flex h-16 shrink-0 items-center">
								<img
									class="h-8 w-auto"
									src="https://tailwindui.com/img/logos/mark.svg?color=indigo&shade=500"
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
															? 'bg-gray-800 text-white'
															: 'text-gray-400 hover:text-white hover:bg-gray-800',
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
									<!-- <li>
										<div class="text-xs font-semibold leading-6 text-gray-400">
											Your teams
										</div>
										<ul role="list" class="-mx-2 mt-2 space-y-1">
											<li v-for="team in teams" :key="team.name">
												<a
													:href="team.href"
													:class="[
														team.current
															? 'bg-gray-800 text-white'
															: 'text-gray-400 hover:text-white hover:bg-gray-800',
														'group flex gap-x-3 rounded-md p-2 text-sm leading-6 font-semibold',
													]"
												>
													<span
														class="flex h-6 w-6 shrink-0 items-center justify-center rounded-lg border border-gray-700 bg-gray-800 text-[0.625rem] font-medium text-gray-400 group-hover:text-white"
														>{{ team.initial }}</span
													>
													<span class="truncate">{{ team.name }}</span>
												</a>
											</li>
										</ul>
									</li> -->
									<li class="-mx-6 mt-auto">
										<a
											href="#"
											class="flex items-center gap-x-4 px-6 py-3 text-sm font-semibold leading-6 text-white hover:bg-gray-800"
										>
											<img
												class="h-8 w-8 rounded-full bg-gray-800"
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
					</DialogPanel>
				</TransitionChild>
			</div>
		</Dialog>
	</TransitionRoot>
</template>

<script setup>
import { ref } from 'vue';
import { Dialog, DialogPanel, TransitionChild, TransitionRoot, XMarkIcon } from '@headlessui/vue';
import {
	ChartBarSquareIcon,
	Cog6ToothIcon,
	FolderIcon,
	GlobeAltIcon,
	ServerIcon,
	SignalIcon,

} from "@heroicons/vue/24/outline";
const sidebarOpen = ref(false);
const navigation = [
	{ name: "Projects", href: "#", icon: FolderIcon, current: false },
	{ name: "Deployments", href: "#", icon: ServerIcon, current: true },
	{ name: "Activity", href: "#", icon: SignalIcon, current: false },
	{ name: "Domains", href: "#", icon: GlobeAltIcon, current: false },
	{ name: "Usage", href: "#", icon: ChartBarSquareIcon, current: false },
	{ name: "Settings", href: "#", icon: Cog6ToothIcon, current: false },
];
</script>
