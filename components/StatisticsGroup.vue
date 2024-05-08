<template>
	<dl class="grid grid-cols-1 gap-px bg-gray-900/5 sm:grid-cols-2">
		<div
			v-for="stat in stats"
			:key="stat.name"
			class="flex flex-wrap items-baseline justify-between gap-x-4 gap-y-2 bg-white px-4 py-6"
		>
			<dt class="text-sm font-medium leading-6 text-gray-900">
				{{ stat.name }}
			</dt>

			<dd
				class="w-full flex-none text-3xl font-medium leading-10 tracking-tight text-yellow-500"
			>
				{{ stat.value }}
			</dd>
		</div>
	</dl>
</template>

<script setup>
const stats = [
	{
		name: "Total Employees",
		value: "1,250",
		change: "+2%",
		changeType: "positive",
	},
	{
		name: "Vacation Days Used",
		value: "4,892 days",
		change: "+5.5%",
		changeType: "negative",
	},
	{
		name: "Training Hours This Year",
		value: "3,500 hours",
		change: "+20%",
		changeType: "positive",
	},
	{
		name: "Employee Turnover Rate",
		value: "15%",
		change: "-3%",
		changeType: "positive",
	},
];
</script>
