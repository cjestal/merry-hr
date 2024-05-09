<template>
	<SitePage>
		<PageHeader
			title="Leave Management"
			description="Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quos."
		/>
		<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4">
			<div
				v-for="stat in stats"
				:key="stat.name"
				class="p-4 border rounded-md w-auto bg-white flex-auto flex shadow-md"
			>
				<div class="flex flex-col justify-between w-full">
					<h3 class="text-sm text-gray-500">Remaining</h3>
					<div class="text-gray-600 text-xl font-semibold">
						{{ stat.name }}
					</div>
				</div>
				<div
					class="flex flex-col justify-center align-middle  text-4xl font-semibold"
					:class="`text-${stat.color}`"
				>
					{{ stat.total }}
				</div>
			</div>
		</div>
	</SitePage>
</template>

<script setup>
const stats = [
	{
		name: "Sick Leave",
		remaining: 5,
		total: 10,
		color: "red-500",
	},
	{
		name: "Casual Leave",
		remaining: 3,
		total: 10,
		color: "yellow-500",
	},
	{
		name: "Earned Leave",
		remaining: 7,
		total: 15,
		color: "green-500",
	},
	{
		name: "Annual Leave",
		remaining: 4,
		total: 20,
		color: "green-500",
	},
	// {
	// 	name: "Comp Off",
	// 	remaining: 2,
	// 	total: 5,
	// 	color: "red-500",
	// },
];
</script>
