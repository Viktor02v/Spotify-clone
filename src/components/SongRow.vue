<template>
	<li class="flex items-center justify-between rounded-md hover:bg-[#2A2929]" @mouseenter="isHover = true"
		@mouseleave="isHover = false">

		<div class="flex items-center w-full py-1.5">
			<div v-if="isHover" class="w-[40px] ml-[14px] mr-[6px] cursor-pointer ">
				<Play v-if="!isPlaying" fillColor="white" :size="25" @click="useSong.playOrPauseThisSong(artist, track)" />
				<Play v-else-if="isPlaying && currentTrack.name !== track.name" fillColor="white" :size="25"
					@click="useSong.loadSong(artist, track)" />
				<Pause v-else fillColor="white" :size="25" @click="useSong.playOrPauseSong()" />
			</div>
			<div v-else class="text-white w-[40px] font-semibold ml-5 cursor-pointer">
				<span :class="{ 'text-green-500': currentTrack && currentTrack.name === track.name }">
					{{ index }}
				</span>
			</div>
			<div>
				<div class="text-white font-semibold">
					<span :class="{ 'text-green-500 text-[18px]' : currentTrack && currentTrack.name === track.name }">{{ track.name }}
					</span>
				</div>
				<div class="text-white font-semibold text-gray-400"><span
						:class="{ 'text-green-800': currentTrack && currentTrack.name === track.name }">{{ track.author
						}}</span></div>
			</div>
		</div>

		<div class="flex items-center">
			<button v-if="isHover" type="button" class="">
				<Heart fillColor="#1BD760" :size="22" />
			</button>

			<div v-if="isTrackTime" class="text-xs mx-5 text-gray-400">
				{{ isTrackTime }}
			</div>

			<div>
				{{ }}
			</div>
		</div>
	</li>
</template>

<script setup>
import { ref, toRefs, onMounted } from 'vue'

import Play from 'vue-material-design-icons/Play.vue'
import Pause from 'vue-material-design-icons/Pause.vue'
import Heart from 'vue-material-design-icons/Heart.vue'

import { useSongStore } from '../stores/song'
import { storeToRefs } from 'pinia';
const useSong = useSongStore()
const { isPlaying, currentTrack } = storeToRefs(useSong)

let isHover = ref(false)
let isTrackTime = ref(null)
const props = defineProps({
	track: Object,
	artist: Object,
	index: Number,
})

const { track, artist, index, author } = toRefs(props)

onMounted(() => {
	const audio = new Audio(track.value.path);
	audio.addEventListener('loadedmetadata', () => {
		const duration = audio.duration;
		const minutes = Math.floor(duration / 60);
		const seconds = Math.floor(duration % 60);
		const text = audio.audioTracks;
		isTrackTime.value = minutes + ':' + seconds.toString().padStart(2, '0');
	})
})
</script>