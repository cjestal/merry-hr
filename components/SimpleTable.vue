<template>
	<div class="px-4 pb-2 sm:px-6 lg:px-8 border rounded-md shadow-md">
		<div class="sm:flex sm:items-center">
			<div class="sm:flex-auto">
				<!-- <h1 class="text-xl font-semibold leading-6 text-gray-900">{{ title }}</h1> -->
				<!-- <p class="mt-2 text-sm text-gray-700">
					A list of all the users in your account including their name, title,
					email and role.
				</p> -->
			</div>
			<!-- <div class="mt-4 sm:ml-16 sm:mt-0 sm:flex-none">
				<button
					type="button"
					class="block rounded-md bg-yellow-500 px-3 py-2 text-center text-sm font-semibold text-white shadow-sm hover:bg-yellow-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-yellow-600"
				>
					Add user
				</button>
			</div> -->
		</div>
		<div class="mt-8 flow-root">
			<div class="-mx-4 -my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
				<div class="inline-block min-w-full py-2 align-middle sm:px-6 lg:px-8">
					<table class="min-w-full divide-y divide-gray-300">
						<thead>
							<tr>
								<th
									scope="col"
									class="py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-gray-900 sm:pl-0"
								>
									Name
								</th>
								<th
									scope="col"
									class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900"
								>
									Title
								</th>
								<th
									scope="col"
									class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900"
								>
									Email
								</th>
								<th
									scope="col"
									class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900"
								>
									Role
								</th>
								<th scope="col" class="relative py-3.5 pl-3 pr-4 sm:pr-0">
									<span class="sr-only">Edit</span>
								</th>
							</tr>
						</thead>
						<tbody class="divide-y divide-gray-200">
							<tr v-for="person in people" :key="person.email">
								<td
									class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
								>
									{{ person.name }}
								</td>
								<td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">
									{{ person.title }}
								</td>
								<td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">
									{{ person.email }}
								</td>
								<td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">
									{{ person.role }}
								</td>
								<td
									class="relative whitespace-nowrap py-4 pl-3 pr-4 text-right text-sm font-medium sm:pr-0"
								>
									<a href="#" class="text-yellow-600 hover:text-yellow-900"
										>Edit<span class="sr-only">, {{ person.name }}</span></a
									>
								</td>
							</tr>
						</tbody>
					</table>
				</div>
			</div>
		</div>
	</div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  title: String
});

const people = [
	{
		name: "Lindsay Walton",
		title: "Front-end Developer",
		email: "lindsay.walton@example.com",
		role: "Member",
	},
	{
		name: "Courtney Henry",
		title: "Backend Developer",
		email: "courtney.henry@example.com",
		role: "Admin",
	},
	{
		name: "Tom Cook",
		title: "UI Designer",
		email: "tom.cook@example.com",
		role: "Member",
	},
	{
		name: "Whitney Francis",
		title: "DevOps Engineer",
		email: "whitney.francis@example.com",
		role: "Member",
	},
	{
		name: "Leonard Krasner",
		title: "Full Stack Developer",
		email: "leonard.krasner@example.com",
		role: "Admin",
	},
	{
		name: "Floyd Miles",
		title: "Product Manager",
		email: "floyd.miles@example.com",
		role: "Member",
	},
	{
		name: "Emily Selman",
		title: "Data Scientist",
		email: "emily.selman@example.com",
		role: "Member",
	},
	{
		name: "Kristin Watson",
		title: "Software Engineer",
		email: "kristin.watson@example.com",
		role: "Admin",
	},
	{
		name: "Cameron Williamson",
		title: "Sales Manager",
		email: "cameron.williamson@example.com",
		role: "Member",
	},
	{
		name: "Esther Howard",
		title: "Marketing Director",
		email: "esther.howard@example.com",
		role: "Admin",
	},
];
</script>
