<template>
	<div>
		<div class=" ">
			<div
				class="text-center lg:col-start-8 lg:col-end-13 lg:row-start-1 xl:col-start-9"
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
					class="isolate mt-2 grid grid-cols-7 gap-px rounded-lg bg-gray-200 text-sm ring-1 ring-gray-200"
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
								day.isSelected && !day.isToday && 'bg-yellow-500',
							]"
							>{{ day.date.split("-").pop().replace(/^0/, "") }}</time
						>
					</button>
				</div>
			</div>
		</div>
	</div>
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

const meetings = [
	{
		id: 1,
		date: "January 10th, 2022",
		time: "5:00 PM",
		datetime: "2022-01-10T17:00",
		name: "Leslie Alexander",
		imageUrl:
			"https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
		location: "Starbucks",
	},
	// More meetings...
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
