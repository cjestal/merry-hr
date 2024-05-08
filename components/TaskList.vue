<template>
	<h1 class="text-lg font-bold mb-1">Task List</h1>
	<ul role="list" class="divide-y divide-gray-100">
		<li
			v-for="task in tasks"
			:key="task.id"
			class="flex items-center justify-between gap-x-6 py-3"
		>
			<div class="min-w-0">
				<div class="flex items-start gap-x-3">
					<p class="text-sm font-semibold leading-6 text-gray-900">
						{{ task.name }}
					</p>
					<p
						:class="[
							statuses[task.status],
							'rounded-md whitespace-nowrap mt-0.5 px-1.5 py-0.5 text-xs font-medium ring-1 ring-inset',
						]"
					>
						{{ task.status }}
					</p>
				</div>
			</div>
			<div class="flex flex-none items-center gap-x-4">
				<!-- <a
					:href="task.href"
					class="hidden rounded-md bg-white px-2.5 py-1.5 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 hover:bg-gray-50 sm:block"
					>View task<span class="sr-only">, {{ task.name }}</span></a
				> -->
				<Menu as="div" class="relative flex-none">
					<MenuButton
						class="-m-2.5 block p-2.5 text-gray-500 hover:text-gray-900"
					>
						<span class="sr-only">Open options</span>
						<EllipsisVerticalIcon class="h-5 w-5" aria-hidden="true" />
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
							class="absolute right-0 z-10 mt-2 w-32 origin-top-right rounded-md bg-white py-2 shadow-lg ring-1 ring-gray-900/5 focus:outline-none"
						>
							<MenuItem v-slot="{ active }">
								<a
									href="#"
									:class="[
										active ? 'bg-gray-50' : '',
										'block px-3 py-1 text-sm leading-6 text-gray-900',
									]"
									>Edit<span class="sr-only">, {{ task.name }}</span></a
								>
							</MenuItem>
							<MenuItem v-slot="{ active }">
								<a
									href="#"
									:class="[
										active ? 'bg-gray-50' : '',
										'block px-3 py-1 text-sm leading-6 text-gray-900',
									]"
									>Move<span class="sr-only">, {{ task.name }}</span></a
								>
							</MenuItem>
							<MenuItem v-slot="{ active }">
								<a
									href="#"
									:class="[
										active ? 'bg-gray-50' : '',
										'block px-3 py-1 text-sm leading-6 text-gray-900',
									]"
									>Delete<span class="sr-only">, {{ task.name }}</span></a
								>
							</MenuItem>
						</MenuItems>
					</transition>
				</Menu>
			</div>
		</li>
	</ul>
</template>

<script setup>
import { Menu, MenuButton, MenuItem, MenuItems } from "@headlessui/vue";
import { EllipsisVerticalIcon } from "@heroicons/vue/20/solid";

const statuses = {
	Complete: "text-green-700 bg-green-50 ring-green-600/20",
	"In progress": "text-gray-600 bg-gray-50 ring-gray-500/10",
	Archived: "text-yellow-800 bg-yellow-50 ring-yellow-600/20",
};
const tasks = [
	{
		id: 1,
		name: "Update GraphQL API",
		href: "#",
		status: "Complete",
		createdBy: "Leslie Alexander",
		dueDate: "March 17, 2023",
		dueDateTime: "2023-03-17T00:00Z",
	},
	{
		id: 2,
		name: "Implement New Benefits Plan",
		href: "#",
		status: "In progress",
		createdBy: "Leslie Alexander",
		dueDate: "May 5, 2023",
		dueDateTime: "2023-05-05T00:00Z",
	},
	{
		id: 3,
		name: "Design Onboarding Emails",
		href: "#",
		status: "In progress",
		createdBy: "Courtney Henry",
		dueDate: "May 25, 2023",
		dueDateTime: "2023-05-25T00:00Z",
	},
	{
		id: 4,
		name: "Develop iOS App",
		href: "#",
		status: "In progress",
		createdBy: "Leonard Krasner",
		dueDate: "June 7, 2023",
		dueDateTime: "2023-06-07T00:00Z",
	},
	{
		id: 5,
		name: "Redesign Marketing Site",
		href: "#",
		status: "Archived",
		createdBy: "Courtney Henry",
		dueDate: "June 10, 2023",
		dueDateTime: "2023-06-10T00:00Z",
	},
	{
		id: 6,
		name: "Optimize SEO Rankings",
		href: "#",
		status: "In progress",
		createdBy: "Morgan McCoy",
		dueDate: "July 15, 2023",
		dueDateTime: "2023-07-15T00:00Z",
	},
];
</script>
