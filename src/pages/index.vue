<template>
    <div class="h-screen flex flex-col overflow-hidden" style="background-color: #292b2c">
        <div class="flex h-[88vh]">
        <!-- sideBar -->
        <sideBar />
            <div class="w-full h-full relative overflow-y-scroll">
                <div class="w-full sticky top-0 py-3 px-5 flex items-center justify-between"
                    style="background-color: #292b2c">
                    <div class="flex items-center">
                        <button class="rounded-full bg-black w-8 h-8 text-white mr-3 hover:bg-white hover:text-black">
                            <i class="material-icons text-2xl">keyboard_arrow_left</i>
                        </button>
                        <button class="rounded-full bg-black w-8 h-8 text-white hover:bg-white hover:text-black">
                            <i class="material-icons text-2xl">keyboard_arrow_right</i>
                        </button>
                    </div>
                    <div class="relative">
                        <button @click="showDropdown = true"
                            class="bg-light text-white rounded-full p-1 flex item-center bg-black hover:bg-white hover:text-black">
                            <img src="./assets/face.jpeg" class="rounded-full h-6 w-6 mr-3" alt="" />
                            <p class="font-semibold text-xs mt-1">Hamza Randhawa</p>
                            <i v-if="showDropdown === false" class="material-icons mt-0">arrow_drop_down</i>
                            <i v-if="showDropdown === true" class="material-icons mt-0">arrow_drop_up</i>
                        </button>
                        <div v-if="showDropdown === true" class="absolute bg-light w-full rounded mt-1">
                            <button @click="showDropdown = false"
                                class="bg-black focus:outline-none w-full py-2 text-white hover:bg-white hover:text-black border-b border-light">
                                Account
                            </button>
                            <button @click="showDropdown = false"
                                class="bg-black focus:outline-none w-full py-2 text-white hover:bg-white hover:text-black border-black border-light">
                                Log Out
                            </button>
                        </div>
                    </div>
                </div>
                <div class="px-6 py-3">
                    <div class="flex item-center justify-between">
                        <h1 class="pl-2 text-2xl font-semibold text-white tracking-wider hover:underline">
                            Recently Played
                        </h1>
                        <h2 class="pr-8 text-xs text-white uppercase tracking-wider hover:underline">
                            See All
                        </h2>
                    </div>
                    <div class="w-full flex flex-wrap">
                        <songCard v-for="recent in recents" :song="recent"></songCard>
                    </div>
                </div>
                <div class="px-6 py-3">
                    <div class="pl-2">
                        <h1 class="text-2xl font-semibold text-white tracking-wider hover:underline">
                            Made for Hamza
                        </h1>
                        <h2 class="text-sm text-white">
                            Get better recommendations the more you listen.
                        </h2>
                    </div>
                    <div class="w-full flex flex-wrap">
                        <songCard v-for="custom in customs" :song="custom"></songCard>
                    </div>
                </div>
            </div>
        </div>

        <div style="height: 12vh; background-color: #282a3a"
            class="w-full flex items-center justify-between px-3 bg-light border-t border-black">
            <div class="flex item-center w-1/4">
                <div>
                    <h1 class="text-sm text-white tracking-wide">Thoda sa Pyar Hua Ha</h1>
                    <h2 class="text-xs text-white tracking-wide">Old Folks</h2>
                </div>
                <i class="material-icons text-xl text-green-600 mx-4">favorite</i>
                <i class="material-icons text-xl text-white">picture_in_picture_alt</i>
            </div>
            <div class="flex flex-col justify-center items-center w-2/4">
                <div class="flex items-center">
                    <button class="text-white opacity-50 hover:opacity-100">
                        <i class="material-icons text-sm">shuffle</i>
                    </button>
                    <button class="text-white opacity-50 hover:opacity-100 mx-5">
                        <i class="material-icons text-sm">skip_previous</i>
                    </button>
                    <button @click.prevent="playsong(`src/assets/Thoda.mp3`), pause = true"
                        class="flex items-center justify-center rounded-full h-8 w-8 mx-5 border-lightest border text-white opacity-50 hover:opacity-100">
                        <i v-if="pause === false" class="material-icons">play_arrow</i><i v-if="pause === true"
                            class="material-icons">pause</i>
                    </button>
                    <button class="text-white opacity-50 mx-5 hover:opacity-100">
                        <i class="material-icons text-sm">skip_next</i>
                    </button>
                    <button class="text-white opacity-50 hover:opacity-100">
                        <i class="material-icons text-sm">repeat</i>
                    </button>
                </div>
                <div class="w-3/4 flex items-center justify-center mt-3">
                    <p class="text-xs text-white mr-1">1:21</p>
                    <div class="w-full bg-black h-1 rounded-full flex items-center">
                        <div class="h-1 rounded-full bg-green-500" style="width: 18%"></div>
                        <div class="rounded-full h-3 w-3 bg-white shadow"></div>
                    </div>
                    <p class="text-xs text-white ml-1">4:52</p>
                </div>
            </div>
            <div class="flex items-center w-1/4 justify-end">
                <i class="material-icons text-xl text-white opacity-50 hover:opacity-100">playlist_play</i>
                <i class="material-icons text-xl text-white mx-3 opacity-50 hover:opacity-100">important_devices</i>
                <i class="material-icons text-xl text-white opacity-50 hover:opacity-100">volume_up</i>
                <div class="w-20 ml-1 bg-white rounded-full h-1"></div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from "vue";
import songCard from "../components/songCard.vue";
import sideBar from "../components/sideBar.vue";

const pages = ref([
    { id: "home", name: "Home", icon: "home" },
    { id: "search", name: "Search", icon: "search" },
    { id: "library", name: "Your Library", icon: "bar_chart" },
]);
const setID = ref("home");

const showDropdown = ref(false);
const recents = ref([
    {
        src: "/src/assets/img1.jpeg",
        title: "Ab tre dil mei",
        artists: "Old folks",
    },
    { src: "/src/assets/img2.jpeg", title: "Pathaan", artists: "T-series" },
    { src: "/src/assets/img3.jpeg", title: "G-Shit", artists: "Moosa_album" },
    { src: "/src/assets/img4.jpeg", title: "Calaboose", artists: "Moosa_album" },
    { src: "/src/assets/img5.jpeg", title: "We Rollins", artists: "Shubh" },
    {
        src: "/src/assets/song1.jpeg",
        title: "Hamari Adhuri Kahani",
        artists: "T-Series",
    },
]);
const customs = ref([
    {
        src: "/src/assets/pic1.jpeg",
        title: "Fallin in love with you",
        artists: "Elvis Presley",
    },
    { src: "/src/assets/pic2.jpeg", title: "Ayat", artists: "T-series" },
    {
        src: "/src/assets/pic3.jpeg",
        title: "Haal e Dil (Female)",
        artists: "T-series",
    },
    {
        src: "/src/assets/pic4.jpeg",
        title: "Tera Chehra",
        artists: "Arijit Singh",
    },
    {
        src: "/src/assets/pic5.jpeg",
        title: "Aint no Grave can hold",
        artists: "Bethel Music",
    },
    { src: "/src/assets/pic6.jpeg", title: "Unstoppable", artists: "Sia" },
]);

const pause = ref(false);

var audio;
function playsong(song) {
    if (song) {
        audio = new Audio(song);
        audio.play();
    }
}
</script>
  