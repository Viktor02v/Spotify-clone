<template>
	<!-- First section: START -->
	<div class="p-8">
		<button type="button" class="text-white text-2xl font-semibold hover:underline cursor-pointer">
			Podcasts to make you smarter
		</button>
		<div class="py-1.5"></div>
		<div class="flex items-center">
			<HomeCard image="https://picsum.photos/id/30/300/300" title="Title is here" subTitle="Subtitle is here" />
			<HomeCard image="https://picsum.photos/id/45/300/300" title="Title is here" subTitle="Subtitle is here" />
			<HomeCard class="md:block hidden" image="https://picsum.photos/id/65/300/300" title="Title is here"
				subTitle="Subtitle is here" />
			<HomeCard class="lg:block hidden" image="https://picsum.photos/id/67/300/300" title="Title is here"
				subTitle="Subtitle is here" />
			<HomeCard class="xl:block hidden" image="https://picsum.photos/id/100/300/300" title="Title is here"
				subTitle="Subtitle is here" />
		</div>
	</div>
	<!-- First section: END -->

	<!-- Second section: START -->
	<div class="p-8">
		<button type="button" class="text-white text-2xl font-semibold hover:underline cursor-pointer">
			Recomended radio
		</button>
		<div class="py-1.5"></div>
		<div class="flex items-center">
			<HomeCard image="https://picsum.photos/id/31/300/300" title="Title is here" subTitle="Subtitle is here" />
			<HomeCard image="https://picsum.photos/id/46/300/300" title="Title is here" subTitle="Subtitle is here" />
			<HomeCard class="md:block hidden" image="https://picsum.photos/id/66/300/300" title="Title is here"
				subTitle="Subtitle is here" />
			<HomeCard class="lg:block hidden" image="https://picsum.photos/id/68/300/300" title="Title is here"
				subTitle="Subtitle is here" />
			<HomeCard class="xl:block hidden" image="https://picsum.photos/id/101/300/300" title="Title is here"
				subTitle="Subtitle is here" />
		</div>
	</div>
	<!-- Second section: END -->

	<!-- Third section: START -->
	<div class="p-8">
		<button type="button" class="text-white text-2xl font-semibold hover:underline cursor-pointer">
			Recomended Songs
		</button>
		<div class="py-1.5"></div>
		<div class="flex items-center">
			<HomeCard image="https://picsum.photos/id/32/300/300" title="Title is here" subTitle="Subtitle is here" />
			<HomeCard image="https://picsum.photos/id/47/300/300" title="Title is here" subTitle="Subtitle is here" />
			<HomeCard class="md:block hidden" image="https://picsum.photos/id/62/300/300" title="Title is here"
				subTitle="Subtitle is here" />
			<HomeCard class="lg:block hidden" image="https://picsum.photos/id/69/300/300" title="Title is here"
				subTitle="Subtitle is here" />
			<HomeCard class="xl:block hidden" image="https://picsum.photos/id/102/300/300" title="Title is here"
				subTitle="Subtitle is here" />
		</div>
	</div>
	<!-- Third section: END -->
</template>
<script setup>
import HomeCard from '../components/HomeCard.vue'
</script>