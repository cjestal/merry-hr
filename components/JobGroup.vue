<template>
	<div class="border-b border-gray-200 bg-white shadow-md rounded-md border">
		<!-- header -->
		<div
			class="border-b border-gray-200 bg-gray-600 px-4 py-5 sm:px-6 rounded-t-md"
		>
			<div
				class="-ml-4 -mt-4 flex flex-wrap items-center justify-between sm:flex-nowrap"
			>
				<div class="ml-4 mt-4">
					<h3 class="text-base font-semibold leading-6 text-white">
						{{ title }}
					</h3>
					<p class="mt-1 text-sm text-gray-200">
						{{ description }}
					</p>
				</div>
				<div class="ml-4 mt-4 flex-shrink-0">
					<button
						type="button"
						class="relative inline-flex items-center rounded-md bg-yellow-500 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-yellow-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-yellow-600"
					>
						Create New Job
					</button>
				</div>
			</div>
		</div>
		<!-- list -->
		<div class="min-h-[200px]">
			<ul
				role="list"
				class="divide-y divide-gray-100 overflow-hidden bg-white shadow-sm ring-1 ring-gray-900/5 sm:rounded-xl"
			>
				<li
					v-for="job in jobs"
					:key="job.description"
					class="relative flex justify-between gap-x-6 px-4 py-5 hover:bg-gray-50 sm:px-6"
				>
					<div class="flex min-w-0 gap-x-4">
						<img
							class="h-12 w-12 flex-none rounded-full bg-gray-50"
							:src="job.imageUrl"
							alt=""
						/>
						<div class="min-w-0 flex-auto">
							<p class="text-sm font-semibold leading-6 text-gray-900">
								<a :href="job.href">
									<span class="absolute inset-x-0 -top-px bottom-0" />
									{{ job.name }}
								</a>
							</p>
							<p class="mt-1 flex text-xs leading-5 text-gray-500">
								<a
									:href="`mailto:${job.description}`"
									class="relative truncate hover:underline"
									>{{ job.description }}</a
								>
							</p>
						</div>
					</div>
					<div class="flex shrink-0 items-center gap-x-4">
						<!-- <div class="hidden sm:flex sm:flex-col sm:items-end">
							<p class="text-sm leading-6 text-gray-900">{{ job.role }}</p>
							<p
								v-if="job.lastSeen"
								class="mt-1 text-xs leading-5 text-gray-500"
							>
								Last seen
								<time :datetime="job.lastSeenDateTime">{{
									job.lastSeen
								}}</time>
							</p>
							<div v-else class="mt-1 flex items-center gap-x-1.5">
								<div class="flex-none rounded-full bg-emerald-500/20 p-1">
									<div class="h-1.5 w-1.5 rounded-full bg-emerald-500" />
								</div>
								<p class="text-xs leading-5 text-gray-500">Online</p>
							</div>
						</div> -->
						<ChevronRightIcon
							class="h-5 w-5 flex-none text-gray-400"
							aria-hidden="true"
						/>
					</div>
				</li>
			</ul>
		</div>
	</div>
</template>

<script setup>
import { ChevronRightIcon } from "@heroicons/vue/20/solid";
import { defineComponent } from "vue";

import { defineProps } from "vue";

defineProps({
	title: {
		type: String,
		default: "Job Group",
	},
	description: {
		type: String,
		default:
			"Lorem ipsum dolor sit amet consectetur adipisicing elit quam corrupti consectetur.",
	},
});
const jobs = [
	{
		name: "Chief Executive Officer",
		description: "Responsible for the overall success of the organization and for making top-level managerial decisions.",
		role: "Co-Founder / CEO",
		imageUrl:
			"https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
		href: "#",
		lastSeen: "3h ago",
		lastSeenDateTime: "2023-01-23T13:23Z",
	},
	{
		name: "Chief Technology Officer",
		description: "Oversees the development and dissemination of technology for external customers, vendors, and other clients to help improve and increase business.",
		role: "Co-Founder / CTO",
		imageUrl:
			"https://images.unsplash.com/photo-1519244703995-f4e0f30006d5?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
		href: "#",
		lastSeen: "3h ago",
		lastSeenDateTime: "2023-01-23T13:23Z",
	},
	{
		name: "Business Relations Manager",
		description: "Manages business relationships with external partners and stakeholders, ensuring productive and professional interactions.",
		role: "Business Relations",
		imageUrl:
			"https://images.unsplash.com/photo-1506794778202-cad84cf45f1d?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
		href: "#",
		lastSeen: null,
	},
	{
		name: "Front-end Engineer",
		description: "Develops and implements the aesthetic design of websites and applications through coding languages like HTML, CSS, and JavaScript.",
		role: "Front-end Developer",
		imageUrl:
			"https://images.unsplash.com/photo-1517841905240-472988babdf9?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
		href: "#",
		lastSeen: "3h ago",
		lastSeenDateTime: "2023-01-23T13:23Z",
	},
	{
		name: "Creative Director",
		description: "Leads the creative team to plan and produce the visual and conceptual direction for product campaigns and branding.",
		role: "Designer",
		imageUrl:
			"https://images.unsplash.com/photo-1438761681033-6461ffad8d80?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
		href: "#",
		lastSeen: "3h ago",
		lastSeenDateTime: "2023-01-23T13:23Z",
	},
	// {
	// 	name: "Product Director",
	// 	description: "Directs the development, implementation, and management of product strategies to ensure the success and profitability of the company’s products.",
	// 	role: "Director of Product",
	// 	imageUrl:
	// 		"https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
	// 	href: "#",
	// 	lastSeen: null,
	// },
];
</script>
