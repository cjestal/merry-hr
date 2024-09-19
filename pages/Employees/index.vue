<template>
	<SitePage>
		<PageHeader
			title="Employee Management"
			description="Add, update, or remove employee details"
		>
			<nuxt-link
				class="block rounded-md bg-yellow-500 px-3 py-2 text-center text-sm font-semibold text-white shadow-sm hover:bg-yellow-400 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-yellow-600"
				to="/employees/new"
				>New Employee</nuxt-link
			>

			<!-- <SiteSlideOver
				label="New Employee"
				title="New Employee"
				buttonType="button"
				description="Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quos."
			/> -->
		</PageHeader>
		<SimpleTable title="Employees" />
	</SitePage>
</template>
