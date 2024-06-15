<template>
	<div>
		<div class="p-8">
			<button type="button" class="text-white text-2xl font-semibold hover:underline cursor-pointer">
				{{ artist.name }}
			</button>
			<div class="py-1.5"></div>

			<!-- AlbumSection: START -->
			<div class="flex items-center h-full relative w-full">
				<img width="140" :src="artist.albumCover" alt="">
				<div class="w-full ml-5">
					<div style="font-size: 33px;"
						class="text-white font-semibold absolute top-0 w-full hover:underline cursor-pointer ">
						{{ artist.name }}
					</div>

					<div class="flex text-gray-300 text-[13px]">
						<div class="flex">Album</div>
						<div class="ml-2 flex">
							<div class="circle mt-2 mr-2" />
							<span class="-ml-0.5">{{ artist.releaseYear }}</span>
						</div>

						<div class="ml-2 flex">
							<div class="circle mt-2 mr-2" />
							<span class="-ml-0.5">{{ artist.tracks.length }} songs</span>
						</div>
					</div>

					<div class="absolute flex gap-4 items-center justify-start bottom-0 mb-1.5">

						<button type="button" class="p-1 rounded-full bg-white" @click="playFunc()">
							<Play v-if="!isPlaying" fillColor="#181818" :size="25" />
							<Pause v-else fillColor="#181818" :size="25" />
						</button>

						<button type="button">
							<Heart fillColor="#1BD760" :size="30" />
						</button>

						<button type="button">
							<DotsHorizontal fillColor="#FFFFFF" :size="25" />
						</button>
					</div>

				</div>
			</div>
			<!-- AlbumSection: END -->
		</div>

		<!-- PlaylistSection: START -->
		<div class="mt-6">
			<div class="flex items-center justify-between px-5 pt-2">

				<div class="flex items-center justify-between text-gray-400">
					<div class="mr-7">#</div>
					<div class="text-sm">Title</div>
				</div>

				<div>
					<!-- <ClockTimeThreeOutLine fillColor="#FFFFFF" :size="18" /> -->
				</div>
			</div>

			<div class="border-b border-b-[#2A2A2A] mt-2"></div>
			<div class="mb-4"></div>

			<ul class="w-full" v-for="track, index in artist.tracks" :key="index">
				<SongRow :artist="artist" :track="track" :index="++index" />
			</ul>
		</div>
		<!-- PlaylistSection: END -->

	</div>
</template>

<script setup>
import SongRow from '../components/SongRow.vue'

import Play from 'vue-material-design-icons/Play.vue'
import Pause from 'vue-material-design-icons/Pause.vue'
import DotsHorizontal from 'vue-material-design-icons/DotsHorizontal.vue'
import Heart from 'vue-material-design-icons/Heart.vue'
// import ClockTimeThreeOutLine from 'vue-material-design-icons/ClockTimeThreeOutLine.vue'
import artist from '../artist.json'

import { useSongStore } from '../stores/song'
import { storeToRefs } from 'pinia';
const useSong = useSongStore()
const { isPlaying, currentTrack, currentArtist } = storeToRefs(useSong)

const playFunc = () => {
	if (currentTrack.value) {
		useSong.playOrPauseThisSong(currentArtist.value, currentTrack.value)
		return
	}
	useSong.playFromFirst()
}
</script>

<style scoped>
.circle {
	width: 4px;
	height: 4px;
	background-color: #fff;
	border-radius: 100%;
}
</style>
