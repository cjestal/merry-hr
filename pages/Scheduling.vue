<template>
	<SitePage>
		<PageHeader
			title="Interview Scheduling"
			description="Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quos."
		/>
		<Card>
			<h2 class="text-base font-semibold leading-6 text-gray-900">
				Upcoming Interviews
			</h2>
			<div class="lg:grid lg:grid-cols-12 lg:gap-x-16">
				<div
					class="mt-10 text-center lg:col-start-8 lg:col-end-13 lg:row-start-1 lg:mt-9 xl:col-start-9"
				>
					<div class="flex items-center text-gray-900">
						<button
							type="button"
							class="-m-1.5 flex flex-none items-center justify-center p-1.5 text-gray-400 hover:text-gray-500"
						>
							<span class="sr-only">Previous month</span>
							<ChevronLeftIcon class="h-5 w-5" aria-hidden="true" />
						</button>
						<div class="flex-auto text-sm font-semibold">January</div>
						<button
							type="button"
							class="-m-1.5 flex flex-none items-center justify-center p-1.5 text-gray-400 hover:text-gray-500"
						>
							<span class="sr-only">Next month</span>
							<ChevronRightIcon class="h-5 w-5" aria-hidden="true" />
						</button>
					</div>
					<div class="mt-6 grid grid-cols-7 text-xs leading-6 text-gray-500">
						<div>M</div>
						<div>T</div>
						<div>W</div>
						<div>T</div>
						<div>F</div>
						<div>S</div>
						<div>S</div>
					</div>
					<div
						class="isolate mt-2 grid grid-cols-7 gap-px rounded-lg bg-gray-200 text-sm shadow ring-1 ring-gray-200"
					>
						<button
							v-for="(day, dayIdx) in days"
							:key="day.date"
							type="button"
							:class="[
								'py-1.5 hover:bg-gray-100 focus:z-10',
								day.isCurrentMonth ? 'bg-white' : 'bg-gray-50',
								(day.isSelected || day.isToday) && 'font-semibold',
								day.isSelected && 'text-white',
								!day.isSelected &&
									day.isCurrentMonth &&
									!day.isToday &&
									'text-gray-900',
								!day.isSelected &&
									!day.isCurrentMonth &&
									!day.isToday &&
									'text-gray-400',
								day.isToday && !day.isSelected && 'text-yellow-500',
								dayIdx === 0 && 'rounded-tl-lg',
								dayIdx === 6 && 'rounded-tr-lg',
								dayIdx === days.length - 7 && 'rounded-bl-lg',
								dayIdx === days.length - 1 && 'rounded-br-lg',
							]"
						>
							<time
								:datetime="day.date"
								:class="[
									'mx-auto flex h-7 w-7 items-center justify-center rounded-full',
									day.isSelected && day.isToday && 'bg-yellow-500',
									day.isSelected && !day.isToday && 'bg-gray-900',
								]"
								>{{ day.date.split("-").pop().replace(/^0/, "") }}</time
							>
						</button>
					</div>
					<div class="mt-8 w-full flex justify-center">
						<SiteSlideOver
							class="mt-2"
							label="Schedule an Interview"
							title="Schedule an Interview"
							description="Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quos."
						/>
					</div>
				</div>
				<ol
					class="mt-4 divide-y divide-gray-100 text-sm leading-6 lg:col-span-7 xl:col-span-8"
				>
					<li
						v-for="interview in interviews"
						:key="interview.id"
						class="relative flex space-x-6 py-6 xl:static"
					>
						<img
							:src="interview.imageUrl"
							alt=""
							class="h-14 w-14 flex-none rounded-full"
						/>
						<div class="flex-auto">
							<h3 class="pr-10 font-semibold text-gray-900 xl:pr-0">
								{{ interview.name }}
							</h3>
							<dl class="mt-2 flex flex-col text-gray-500 xl:flex-row">
								<div class="flex items-start space-x-3">
									<dt class="mt-0.5">
										<span class="sr-only">Date</span>
										<CalendarIcon
											class="h-5 w-5 text-gray-400"
											aria-hidden="true"
										/>
									</dt>
									<dd>
										<time :datetime="interview.datetime"
											>{{ interview.date }} at {{ interview.time }}</time
										>
									</dd>
								</div>
								<div
									class="mt-2 flex items-start space-x-3 xl:ml-3.5 xl:mt-0 xl:border-l xl:border-gray-400 xl:border-opacity-50 xl:pl-3.5"
								>
									<dt class="mt-0.5">
										<span class="sr-only">Location</span>
										<MapPinIcon
											class="h-5 w-5 text-gray-400"
											aria-hidden="true"
										/>
									</dt>
									<dd>{{ interview.location }}</dd>
								</div>
							</dl>
						</div>
						<Menu
							as="div"
							class="absolute right-0 top-6 xl:relative xl:right-auto xl:top-auto xl:self-center"
						>
							<div>
								<MenuButton
									class="-m-2 flex items-center rounded-full p-2 text-gray-500 hover:text-gray-600"
								>
									<span class="sr-only">Open options</span>
									<EllipsisHorizontalIcon class="h-5 w-5" aria-hidden="true" />
								</MenuButton>
							</div>

							<transition
								enter-active-class="transition ease-out duration-100"
								enter-from-class="transform opacity-0 scale-95"
								enter-to-class="transform opacity-100 scale-100"
								leave-active-class="transition ease-in duration-75"
								leave-from-class="transform opacity-100 scale-100"
								leave-to-class="transform opacity-0 scale-95"
							>
								<MenuItems
									class="absolute right-0 z-10 mt-2 w-36 origin-top-right rounded-md bg-white shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none"
								>
									<div class="py-1">
										<MenuItem v-slot="{ active }">
											<a
												href="#"
												:class="[
													active
														? 'bg-gray-100 text-gray-900'
														: 'text-gray-700',
													'block px-4 py-2 text-sm',
												]"
												>Edit</a
											>
										</MenuItem>
										<MenuItem v-slot="{ active }">
											<a
												href="#"
												:class="[
													active
														? 'bg-gray-100 text-gray-900'
														: 'text-gray-700',
													'block px-4 py-2 text-sm',
												]"
												>Cancel</a
											>
										</MenuItem>
									</div>
								</MenuItems>
							</transition>
						</Menu>
					</li>
				</ol>
			</div>
		</Card>
	</SitePage>
</template>

<script setup>
import {
	CalendarIcon,
	ChevronLeftIcon,
	ChevronRightIcon,
	EllipsisHorizontalIcon,
	MapPinIcon,
} from "@heroicons/vue/20/solid";
import { Menu, MenuButton, MenuItem, MenuItems } from "@headlessui/vue";
import SiteSlideOver from "~/components/SiteSlideOver.vue";

const interviews = [
	{
		id: 1,
		date: "May 9th, 2024",
		time: "5:00 PM",
		datetime: "2024-05-09T17:00",
		name: "Leslie Alexander",
		imageUrl:
			"https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
		location: "https://zoom.us/j/1234567890",
	},
	{
		id: 2,
		date: "May 10th, 2024",
		time: "2:00 PM",
		datetime: "2024-05-10T14:00",
		name: "Jordan Walsh",
		imageUrl:
			"https://images.unsplash.com/photo-1544005313-94ddf0286df2?ixlib=rb-1.2.1&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
		location: "Meeting Room A",
	},
	{
		id: 3,
		date: "May 11th, 2024",
		time: "11:00 AM",
		datetime: "2024-05-11T11:00",
		name: "Casey Johnson",
		imageUrl:
			"https://images.unsplash.com/photo-1557804506-669a67965ba0?ixlib=rb-1.2.1&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
		location: "Meeting Room B",
	},
	{
		id: 4,
		date: "May 12th, 2024",
		time: "4:00 PM",
		datetime: "2024-05-12T16:00",
		name: "Avery Stewart",
		imageUrl:
			"https://images.unsplash.com/photo-1544005313-94ddf0286df2?ixlib=rb-1.2.1&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
		location: "https://zoom.us/j/0987654321",
	},
	{
		id: 5,
		date: "May 13th, 2024",
		time: "1:00 PM",
		datetime: "2024-05-13T13:00",
		name: "Jamie Lane",
		imageUrl:
			"https://images.unsplash.com/photo-1557804506-669a67965ba0?ixlib=rb-1.2.1&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
		location: "Meeting Room C",
	},
	{
		id: 6,
		date: "May 14th, 2024",
		time: "10:00 AM",
		datetime: "2024-05-14T10:00",
		name: "Morgan Reese",
		imageUrl:
			"https://images.unsplash.com/photo-1544005313-94ddf0286df2?ixlib=rb-1.2.1&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
		location: "https://zoom.us/j/1122334455",
	},
	{
		id: 7,
		date: "May 15th, 2024",
		time: "3:00 PM",
		datetime: "2024-05-15T15:00",
		name: "Taylor Chris",
		imageUrl:
			"https://images.unsplash.com/photo-1557804506-669a67965ba0?ixlib=rb-1.2.1&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
		location: "Meeting Room D",
	},
	{
		id: 8,
		date: "May 16th, 2024",
		time: "9:00 AM",
		datetime: "2024-05-16T09:00",
		name: "Devon Lane",
		imageUrl:
			"https://images.unsplash.com/photo-1544005313-94ddf0286df2?ixlib=rb-1.2.1&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
		location: "Meeting Room E",
	},
	{
		id: 9,
		date: "May 17th, 2024",
		time: "12:00 PM",
		datetime: "2024-05-17T12:00",
		name: "Pat Alex",
		imageUrl:
			"https://images.unsplash.com/photo-1557804506-669a67965ba0?ixlib=rb-1.2.1&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
		location: "https://zoom.us/j/5566778899",
	},
];
const days = [
	{ date: "2021-12-27" },
	{ date: "2021-12-28" },
	{ date: "2021-12-29" },
	{ date: "2021-12-30" },
	{ date: "2021-12-31" },
	{ date: "2022-01-01", isCurrentMonth: true },
	{ date: "2022-01-02", isCurrentMonth: true },
	{ date: "2022-01-03", isCurrentMonth: true },
	{ date: "2022-01-04", isCurrentMonth: true },
	{ date: "2022-01-05", isCurrentMonth: true },
	{ date: "2022-01-06", isCurrentMonth: true },
	{ date: "2022-01-07", isCurrentMonth: true },
	{ date: "2022-01-08", isCurrentMonth: true },
	{ date: "2022-01-09", isCurrentMonth: true },
	{ date: "2022-01-10", isCurrentMonth: true },
	{ date: "2022-01-11", isCurrentMonth: true },
	{ date: "2022-01-12", isCurrentMonth: true, isToday: true },
	{ date: "2022-01-13", isCurrentMonth: true },
	{ date: "2022-01-14", isCurrentMonth: true },
	{ date: "2022-01-15", isCurrentMonth: true },
	{ date: "2022-01-16", isCurrentMonth: true },
	{ date: "2022-01-17", isCurrentMonth: true },
	{ date: "2022-01-18", isCurrentMonth: true },
	{ date: "2022-01-19", isCurrentMonth: true },
	{ date: "2022-01-20", isCurrentMonth: true },
	{ date: "2022-01-21", isCurrentMonth: true },
	{ date: "2022-01-22", isCurrentMonth: true, isSelected: true },
	{ date: "2022-01-23", isCurrentMonth: true },
	{ date: "2022-01-24", isCurrentMonth: true },
	{ date: "2022-01-25", isCurrentMonth: true },
	{ date: "2022-01-26", isCurrentMonth: true },
	{ date: "2022-01-27", isCurrentMonth: true },
	{ date: "2022-01-28", isCurrentMonth: true },
	{ date: "2022-01-29", isCurrentMonth: true },
	{ date: "2022-01-30", isCurrentMonth: true },
	{ date: "2022-01-31", isCurrentMonth: true },
	{ date: "2022-02-01" },
	{ date: "2022-02-02" },
	{ date: "2022-02-03" },
	{ date: "2022-02-04" },
	{ date: "2022-02-05" },
	{ date: "2022-02-06" },
];
</script>
