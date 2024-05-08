<template>
	<h1 class="text-lg font-bold mb-2">Latest Updates</h1>
	<ul role="list" class="divide-y divide-gray-100">
		<li v-for="item in updates" :key="item.commit" class="py-2">
			<div class="flex items-center justify-start gap-x-3">
				<img
					:src="item.user.imageUrl"
					alt=""
					class="h-6 w-6 flex-none rounded-full bg-gray-800"
				/>
				<h3
					class="flex truncate text-sm font-semibold leading-6 text-gray-900 min-w-[120px]"
				>
					{{ item.user.name }}
				</h3>
				<p class="truncate text-sm text-gray-500 flex-auto">
					Pushed to
					<span class="text-gray-700">{{ item.projectName }}</span> (<span
						class="font-mono text-gray-700"
						>{{ item.commit }}</span
					>
					on <span class="text-gray-700">{{ item.branch }}</span
					>)
				</p>
				<time
					:datetime="item.dateTime"
					class="flex-none text-xs text-gray-500"
					>{{ item.date }}</time
				>
			</div>
		</li>
	</ul>
</template>

<script setup>
const updates = [
	{
		user: {
			name: "Michael Foster",
			imageUrl:
				"https://images.unsplash.com/photo-1519244703995-f4e0f30006d5?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
		},
		projectName: "Employee Onboarding",
		commit: "HR20230123",
		branch: "HR Policies",
		date: "1h",
		dateTime: "2023-01-23T11:00",
	},
	{
		user: {
			name: "Lindsay Walton",
			imageUrl:
				"https://images.unsplash.com/photo-1517841905240-472988babdf9?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
		},
		projectName: "Annual Reviews",
		commit: "HR249df660",
		branch: "Performance",
		date: "3h",
		dateTime: "2023-01-23T09:00",
	},
	{
		user: {
			name: "Courtney Henry",
			imageUrl:
				"https://images.unsplash.com/photo-1438761681033-6461ffad8d80?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
		},
		projectName: "Diversity Training",
		commit: "HR11464223",
		branch: "Training Programs",
		date: "12h",
		dateTime: "2023-01-23T00:00",
	},
	{
		user: {
			name: "Courtney Henry",
			imageUrl:
				"https://images.unsplash.com/photo-1438761681033-6461ffad8d80?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
		},
		projectName: "Salary Adjustments",
		commit: "HRdad28e95",
		branch: "Compensation",
		date: "2d",
		dateTime: "2023-01-21T13:00",
	},
	{
		user: {
			name: "Leslie Alexander",
			imageUrl:
				"https://images.unsplash.com/photo-1573497491208-6b1acb260507?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
		},
		projectName: "New Benefits Plan",
		commit: "HR2023BEN01",
		branch: "Benefits",
		date: "5d",
		dateTime: "2023-01-18T08:00",
	},
];
</script>
