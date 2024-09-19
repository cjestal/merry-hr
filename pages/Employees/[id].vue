<template>
	<SitePage>
		<PageHeaderWithTabs
			title="Employee Details"
			description="View and manage employee details"
			:tabs="tabs"
		/>
		<NuxtPage />
	</SitePage>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { useRoute } from 'vue-router';
import Card from '@/components/Card.vue';
import Actions from '@/components/Actions.vue';
const route = useRoute();
const employee = ref(null);

const tabs = ref([
	{
		name: 'Overview',
		href: `overview`,
		current: true
	},
	{
		name: 'Performance',
		href: `performance`,
		current: false
	},
	{
		name: 'Documents',
		href: `/employees/${route.params.id}/documents`,
		current: false
	},
	{
		name: 'History',
		href: `/employees/${route.params.id}/history`,
		current: false
	}
]);



onMounted(async () => {
	const employeeId = route.params.id;
	// Fetch employee data here
	// For example:
	// employee.value = await fetchEmployeeData(employeeId);
	
	// Placeholder data for demonstration
	employee.value = {
		id: employeeId,
		name: 'John Doe',
		email: 'john.doe@example.com',
		position: 'Software Developer'
	};
});
</script>
