<template>
	<SitePage>
		<div class="space-y-6">
			<Card v-if="employee">
				<template #title>Employee Information</template>
				<template #content>
					<dl class="grid grid-cols-1 gap-x-4 gap-y-8 sm:grid-cols-2">
						<div class="sm:col-span-1">
							<dt class="text-sm font-medium text-gray-500">Full name</dt>
							<dd class="mt-1 text-sm text-gray-900">{{ employee.name }}</dd>
						</div>
						<div class="sm:col-span-1">
							<dt class="text-sm font-medium text-gray-500">Email address</dt>
							<dd class="mt-1 text-sm text-gray-900">{{ employee.email }}</dd>
						</div>
						<div class="sm:col-span-1">
							<dt class="text-sm font-medium text-gray-500">Position</dt>
							<dd class="mt-1 text-sm text-gray-900">{{ employee.position }}</dd>
						</div>
						<div class="sm:col-span-1">
							<dt class="text-sm font-medium text-gray-500">Employee ID</dt>
							<dd class="mt-1 text-sm text-gray-900">{{ employee.id }}</dd>
						</div>
					</dl>
				</template>
			</Card>

			<Actions>
				<template #actions>
					<button
						type="button"
						class="inline-flex items-center rounded-md bg-white px-3 py-2 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 hover:bg-gray-50"
					>
						Edit
					</button>
				</template>
			</Actions>
		</div>
	</SitePage>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { useRoute } from 'vue-router';
import Card from '@/components/Card.vue';
import Actions from '@/components/Actions.vue';
import SitePage from '@/components/SitePage.vue';

const route = useRoute();
const employee = ref(null);

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

