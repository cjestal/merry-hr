<template>
	<ul role="list" class="divide-y divide-gray-100">
		<li
			v-for="project in applicants"
			:key="project.id"
			class="flex items-center justify-between gap-x-6 py-5"
		>
			<div class="min-w-0">
				<div class="flex items-start gap-x-3">
					<p class="text-sm font-semibold leading-6 text-gray-900">
						{{ project.name }}
					</p>
					<p
						:class="[
							positiones[project.position],
							'rounded-md whitespace-nowrap mt-0.5 px-1.5 py-0.5 text-xs font-medium ring-1 ring-inset',
						]"
					>
						{{ project.position }}
					</p>
				</div>
				<div
					class="mt-1 flex items-center gap-x-2 text-xs leading-5 text-gray-500"
				>
					<p class="whitespace-nowrap">
						Applied on
						<time :datetime="project.dueDateTime">{{ project.dueDate }}</time>
					</p>
					<svg viewBox="0 0 2 2" class="h-0.5 w-0.5 fill-current">
						<circle cx="1" cy="1" r="1" />
					</svg>
					<!-- <p class="truncate">Created by {{ project.createdBy }}</p> -->
				</div>
			</div>
			<div class="flex flex-none items-center gap-x-4">
				<!-- <a
					:href="project.href"
					class="hidden rounded-md bg-white px-2.5 py-1.5 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 hover:bg-gray-50 sm:block"
					>View Applicant<span class="sr-only">, {{ project.name }}</span></a
				> -->
				<SiteSlideOver
					label="View Applicant"
					title="Applicant Details"
					description="Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quos."
				/>
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
									>Edit<span class="sr-only">, {{ project.name }}</span></a
								>
							</MenuItem>
							<MenuItem v-slot="{ active }">
								<a
									href="#"
									:class="[
										active ? 'bg-gray-50' : '',
										'block px-3 py-1 text-sm leading-6 text-gray-900',
									]"
									>Move<span class="sr-only">, {{ project.name }}</span></a
								>
							</MenuItem>
							<MenuItem v-slot="{ active }">
								<a
									href="#"
									:class="[
										active ? 'bg-gray-50' : '',
										'block px-3 py-1 text-sm leading-6 text-gray-900',
									]"
									>Delete<span class="sr-only">, {{ project.name }}</span></a
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

const positiones = {
	"Software Engineer": "text-green-700 bg-green-50 ring-green-600/20",
	"Project Manager": "text-gray-600 bg-gray-50 ring-gray-500/10",
	"UI/UX Designer": "text-yellow-800 bg-yellow-50 ring-yellow-600/20",
	"Data Analyst": "text-blue-700 bg-blue-50 ring-blue-600/20",
	"Marketing Specialist": "text-purple-700 bg-purple-50 ring-purple-600/20",
};
const applicants = [
	{
		id: 1,
		name: "Ava Smith",
		href: "#",
		position: "Software Engineer",
		createdBy: "Leslie Alexander",
		dueDate: "March 17, 2023",
		dueDateTime: "2023-03-17T00:00Z",
	},
	{
		id: 2,
		name: "Liam Johnson",
		href: "#",
		position: "Project Manager",
		createdBy: "Leslie Alexander",
		dueDate: "May 5, 2023",
		dueDateTime: "2023-05-05T00:00Z",
	},
	{
		id: 3,
		name: "Emma Williams",
		href: "#",
		position: "UI/UX Designer",
		createdBy: "Courtney Henry",
		dueDate: "May 25, 2023",
		dueDateTime: "2023-05-25T00:00Z",
	},
	{
		id: 4,
		name: "Noah Jones",
		href: "#",
		position: "Data Analyst",
		createdBy: "Leonard Krasner",
		dueDate: "June 7, 2023",
		dueDateTime: "2023-06-07T00:00Z",
	},
	{
		id: 5,
		name: "Oliver Garcia",
		href: "#",
		position: "Marketing Specialist",
		createdBy: "Courtney Henry",
		dueDate: "June 10, 2023",
		dueDateTime: "2023-06-10T00:00Z",
	},
	{
		id: 6,
		name: "Isabella Martinez",
		href: "#",
		position: "Software Engineer",
		createdBy: "Leslie Alexander",
		dueDate: "July 15, 2023",
		dueDateTime: "2023-07-15T00:00Z",
	},
	{
		id: 7,
		name: "Mason Rodriguez",
		href: "#",
		position: "Project Manager",
		createdBy: "Leslie Alexander",
		dueDate: "August 20, 2023",
		dueDateTime: "2023-08-20T00:00Z",
	},
	{
		id: 8,
		name: "Sophia Davis",
		href: "#",
		position: "UI/UX Designer",
		createdBy: "Courtney Henry",
		dueDate: "September 30, 2023",
		dueDateTime: "2023-09-30T00:00Z",
	},
	{
		id: 9,
		name: "Jacob Wilson",
		href: "#",
		position: "Data Analyst",
		createdBy: "Leonard Krasner",
		dueDate: "October 18, 2023",
		dueDateTime: "2023-10-18T00:00Z",
	},
	{
		id: 10,
		name: "Mia Anderson",
		href: "#",
		position: "Marketing Specialist",
		createdBy: "Courtney Henry",
		dueDate: "November 12, 2023",
		dueDateTime: "2023-11-12T00:00Z",
	}
];
</script>
