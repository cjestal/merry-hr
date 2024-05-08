<template>
	<SitePage>
		<PageHeader title="Dashboard" />
		<!-- <Actions /> -->
		<div class="grid grid-cols-1 md:grid-cols-2 gap-4">
			<Card>
				<StatisticsGroup />
			</Card>
			<Card>
				<UpdatesList />
			</Card>
			<Card>
				<TaskList />
			</Card>
			<Card>
				<Calendar />
			</Card>
		</div>
	</SitePage>
</template>
