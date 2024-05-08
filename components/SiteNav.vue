<template>
	<div
		class="hidden xl:fixed xl:inset-y-0 xl:z-50 xl:flex xl:w-72 xl:flex-col bg-gray-600"
	>
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
				<ul role="list" class="flex flex-1 flex-col gap-y-2">
					<li v-for="item in navigation" :key="item.name">
						<NuxtLink
							:to="item.href"
							:class="[
								isCurrentRoute(item.href)
									? 'bg-yellow-500 text-white'
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
						</NuxtLink>
						<ul v-if="item.subNavigation" class="pl-4 mt-2 space-y-1">
							<li v-for="subItem in item.subNavigation" :key="subItem.name">
								<NuxtLink
									:to="subItem.href"
									:class="[
										isCurrentRoute(subItem.href)
											? 'bg-yellow-500 text-white'
											: 'text-gray-400 hover:text-white hover:bg-gray-700',
										'group flex gap-x-3 rounded-md p-2 text-sm leading-6 font-semibold',
									]"
								>
									{{ subItem.name }}
								</NuxtLink>
							</li>
						</ul>
					</li>
					<li class="-mx-6 mt-auto">
						<NuxtLink
							to="#"
							class="flex items-center gap-x-4 px-6 py-3 text-sm font-semibold leading-6 text-white hover:bg-gray-700"
						>
							<img
								class="h-8 w-8 rounded-full bg-gray-700"
								src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
								alt=""
							/>
							<span class="sr-only">Your profile</span>
							<span aria-hidden="true">Clint James</span>
						</NuxtLink>
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
	ClockIcon,
	QuestionMarkCircleIcon,
} from "@heroicons/vue/24/outline";
import { useRoute } from "vue-router";

const route = useRoute();

const navigation = [
	{ name: "Dashboard", href: "/", icon: ServerIcon },
	{
		name: "Benefits Administration",
		href: "/benefits",
		icon: ChartBarSquareIcon,
		subNavigation: [
			{ name: "Assistance Programs", href: "/assistance" },
			{ name: "Benefits Enrollment", href: "/enrollment" },
			{ name: "Insurance Management", href: "/insurance" },
			{ name: "Retirement Plans", href: "/retirement" },
		],
	},
	{
		name: "Compliance & Policies",
		href: "/compliance",
		icon: Cog6ToothIcon,
		subNavigation: [
			{ name: "Document Management", href: "/documents" },
			{ name: "HR Policies and Procedures", href: "/policies" },
			{ name: "Legal Compliance", href: "/legal" },
		],
	},
	{ name: "Employee Management", href: "/employees", icon: FolderIcon },
	{
		name: "Help and Support",
		href: "/support",
		icon: QuestionMarkCircleIcon,
		subNavigation: [
			{ name: "FAQs", href: "/faqs" },
			{ name: "User Guides and Tutorials", href: "/guides" },
		],
	},
	{
		name: "Recruitment",
		href: "/recruitment",
		icon: SignalIcon,
		subNavigation: [
			{ name: "Applicant Tracking", href: "/tracking" },
			{ name: "Candidate Evaluation", href: "/evaluation" },
			{ name: "Interview Scheduling", href: "/scheduling" },
			{ name: "Job Postings", href: "/postings" },
		],
	},
	{
		name: "Settings",
		href: "/settings",
		icon: Cog6ToothIcon,
		subNavigation: [
			{ name: "Account Settings", href: "/account" },
			{ name: "Integration Options", href: "/integration" },
			{ name: "Permissions", href: "/permissions" },
		],
	},
	{
		name: "Training & Development",
		href: "/training",
		icon: GlobeAltIcon,
		subNavigation: [
			{ name: "Attendance & Completion", href: "/completion" },
			{ name: "Skill Development Plans", href: "/skills" },
			{ name: "Training Programs/Courses", href: "/courses" },
		],
	},
	{
		name: "Attendance",
		href: "/attendance",
		icon: ClockIcon,
		subNavigation: [
			{ name: "Clock-In/Clock-Out", href: "/clock" },
			{ name: "Leave Management", href: "/leave" },
			{ name: "Timesheets", href: "/timesheets" },
		],
	},
];

function isCurrentRoute(href) {
	if (href === '/') {
		return route.path === '/';
	}
	return route.path.startsWith(href);
}
</script>
