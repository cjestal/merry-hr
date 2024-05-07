<template>
	<SitePage>
		<PageHeaderWithTabs
			title="Applicant Tracking"
			description="Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quos."
			:tabs="tabs"
		/>
		<NuxtPage />
	</SitePage>
</template>

<script setup>
const tabs = [
	{ name: "Applied", href: "/tracking/applied", current: false },
	{ name: "Phone Screening", href: "/tracking/screening", current: false },
	{ name: "Interview", href: "/tracking/interview", current: true },
	{ name: "Offer", href: "/tracking/offer", current: false },
	{ name: "Hired", href: "/tracking/hired", current: false },
];
</script>
