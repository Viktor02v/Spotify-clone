<template>
	<VolumeMute v-if="vol == 0" fillColor="white" :size="20" />
	<VolumeHigh v-else fillColor="white" :size="20" />
	<div class="flex items-center ml-2 mt-2 w-[150px] relative mb-[23px]" @mouseenter="isHover = true"
		@mouseleave="isHover = false">
		<input v-model="vol" type="range" ref="volume"
			class="absolute rounded-full my-2 mt-[24px] w-full h-0 z-40 appearance-none bg-oppacity-100  focus:outline-none accent-white"
			:class="{ 'rangeDotHidden': !isHover }" />
		<div class="pointer-events-none absolute inset-y-0 mt-[6px] w-0 left-0 z-10 h-[4px]" :style="`width: ${vol}%;`"
			:class="isHover ? 'bg-blue-500' : 'bg-white'" />
		<div class="absolute h-[4px] z-[-0] mt-[6px] inset-y-0 left-0 w-full bg-gray-500 rounded-full" />
	</div>
</template>
<script setup>
import { ref, onMounted } from 'vue'

import VolumeMute from 'vue-material-design-icons/VolumeMute.vue'
import VolumeHigh from 'vue-material-design-icons/VolumeHigh.vue'

import { useSongStore } from '../stores/song'
import { storeToRefs } from 'pinia';
const useSong = useSongStore()
const { audio } = storeToRefs(useSong)

let isHover = ref(false)
let vol = ref(80)
let volume = ref(null)

onMounted(() => {
	volume.value.addEventListener('input', (e) => {
		audio.value.volume = e.currentTarget.value / 100;
	})
})
</script>

<style>
.rangeDotHidden[type='range']::-webkit-slider-thumb {
	-webkit-appearance: none;
	appearance: none;
	width: 0;
	height: 0
}
</style>
