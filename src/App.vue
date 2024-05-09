<template>
	<div>
		<div
			class="flex items-center justify-between w-[calc(100%-240px)] h-[60px] fixed right-0 z-20 bg-black bg-opacity-80 ">
			<!-- Buttons: START -->
			<div class="flex items-center ml-6">
				<button type="button" class="rounded-full bg-black p-[1px] cursor-pointer">
					<ChevronLeft fillColor="white" :size="30" />
				</button>
				<button type="button" class="rounded-full bg-black p-[1px] ml-4 cursor-pointer">
					<ChevronRight fillColor="white" :size="30" />
				</button>
			</div>
			<!-- Buttons: END -->

			<!-- Profile: START -->
			<button @click="openMenu = !openMenu" :class="openMenu ? 'bg-[#282828]' : 'bg-black'"
				class="hover:bg-[#282828] rounded-full p-0.5 mr-8 mt-0.5 cursor-pointer ">
				<div class="flex items-center">
					<img class="rounded-full" width="27"
						src="https://yt3.googleusercontent.com/ytc/AIdro_lsZOCWR8cFCsIL6oumZ22l1qOw5yEKXK45HIK9sl0KJes=s176-c-k-c0x00ffffff-no-rj"
						alt="">
					<div class="text-white text-[14px] ml-1.5 font-semibold">Viktor Petruk</div>
					<ChevronDown v-if="!openMenu" @click="openMenu = true" fillColor="white" :size="25" />
					<ChevronUp v-else @click="openMenu = false" fillColor="white" :size="25" />
				</div>
			</button>
			<!-- Profile: END -->

			<!-- Menu: START -->
			<span v-if="openMenu"
				class="fixed w-[170px] bg-[#282828] shadow-2xl z-50 rounded-sm top-[52px] right-[35px] p-1 cursor-pointer">
				<ul class="text-gray-200 font-semibold text-[14px]">
					<li class="px-3 py-2.5 hover:bg-[#3E3D3D] border-b border-b-gray-600">Profile</li>
					<li class="px-3 py-2.5 hover:bg-[#3E3D3D] ">Log out</li>
				</ul>
			</span>
			<!--Menu: END  -->
		</div>

		<!-- Side nav: START -->
		<div id="sideNav" class="h-[100%] p-6 w-[240px] fixed z-50 bg-black">
			<RouterLink to="/">
				<img width="125" src="/icons/spotify-logo.png" alt="">
			</RouterLink>
			<div class="my-8"></div>
			<ul>
				<RouterLink to="/">
					<MenuItem class="ml-[1px]" :icon-size="23" name="Home" :icon-string="'home'" pageUrl="/" />
				</RouterLink>
				<RouterLink to="/search">
					<MenuItem class="ml-[1px]" :icon-size="24" name="Search" :icon-string="'search'" pageUrl="/search" />
				</RouterLink>
				<RouterLink to="/library">
					<MenuItem class="ml-[2px]" :icon-size="23" name="Library" :icon-string="'library'" pageUrl="/library" />
				</RouterLink>
				<div class="py-3.5"></div>
				<MenuItem :icon-size="24" name="Create playlist" :icon-string="'playlist'" pageUrl="/episodes" />
				<MenuItem class="-ml-[1px]" :icon-size="27" name="Liked songs" :icon-string="'liked'" pageUrl="/liked" />
			</ul>
			<div class="border-b border-b-gray-700"></div>
			<ul>
				<li class="font-semibold text-gray-300 text-[13px] mt-3 hover:text-white">My playlists #1</li>
				<li class="font-semibold text-gray-300 text-[13px] mt-3 hover:text-white">My playlists #2</li>
				<li class="font-semibold text-gray-300 text-[13px] mt-3 hover:text-white">My playlists #3</li>
				<li class="font-semibold text-gray-300 text-[13px] mt-3 hover:text-white">My playlists #4</li>
			</ul>
		</div>
		<!-- Side nav: END -->
	</div>

	<!-- Main content: START -->
	<div class="fixed right-0 top-0 w-[calc(100%-240px)] h-full overflow-auto bg-gradient-to-b from-[#1C1C1C] to-black ">
		<div class="mt-[70px]">
			<RouterView />
			<div class="mt-[100px]"></div>
		</div>
	</div>
	<!-- Main content: END -->
	<MusicPlayer v-if="currentTrack" />
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { RouterView, RouterLink } from 'vue-router'

import MusicPlayer from './components/MusicPlayer.vue'
import MenuItem from './components/MenuItem.vue'

import ChevronUp from 'vue-material-design-icons/ChevronUp.vue'
import ChevronDown from 'vue-material-design-icons/ChevronDown.vue'
import ChevronRight from 'vue-material-design-icons/ChevronRight.vue'
import ChevronLeft from 'vue-material-design-icons/ChevronLeft.vue'

import { useSongStore } from './stores/song'
import { storeToRefs } from 'pinia';
const useSong = useSongStore()
const { isPlaying, currentTrack } = storeToRefs(useSong)

let openMenu = ref(false)

onMounted(() => {
	isPlaying.value = false
}
)
</script>