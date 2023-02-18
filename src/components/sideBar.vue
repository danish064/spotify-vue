<template>
    <div class="w-56 bg-black h-full flex-none">
        <div class="p-6">
            <img src="./assets/spotify-1.svg" class="h-10" style="filter: brightness(0) invert(1)" />
        </div>
        <div class="mx-2 mb-5">
            <!-- <button v-for="page in pages" @click="setID = page.id" :class="`w-full text-white text-sm font-semibold rounded  bg-black hover:bg-white hover:text-black px-3 py-2 flex item-center justify-start ${setID === page.id ? 'bg-light' : ''
                }`">
                <i class="material-icons mr-3">{{ page.icon }}</i>
                <p>{{ page.name }}</p>
            </button> -->
            <button
                class="`w-full text-white text-sm font-semibold rounded  bg-black hover:bg-white hover:text-black px-3 py-2 flex item-center justify-start">
                <i class="material-icons mr-3">home</i>
                <p>Home</p>
            </button>
        </div>
        <div class="mx-5">
            <h1 class="text-xs text-lightes`t tracking widest uppercase" style="color: white">
                P l a y l i s t s
            </h1>
            <button class="flex item-centre justify-start opacity-75 hover:opacity-100">
                <i class="material-icons mt-3" style="color: white">add_box</i>
                <p class="text-sm text-white font-semibold mt-3.5 ml-3">
                    Create Playlist
                </p>
            </button>
            <button class="flex item-centre justify-start opacity-75 hover:opacity-100">
                <i class="material-icons mt-3" style="color: red">favorite</i>
                <p class="text-sm text-white font-semibold mt-3.5 ml-3">
                    Liked Songs
                </p>
            </button>
            <div class="h-px w-full bg-light my-3 mt-4" style="color: white">
                <hr />
            </div>
        </div>
        <div class="mx-5">
            <div class="w-full">
                <p v-for="album in albums" class="text-lightest opacity-75 hover:opacity-100 text-sm py-1"
                    style="color: white">
                    {{ album.name }}
                </p>
            </div>
            <button class="flex item-center justify-start opacity-75 hover:opacity-100 mt-4" style="color: white">
                <i class="material-icons rounded-full border border-white-300 text-sm"
                    style="color: white">arrow_downward</i>
                <p class="text-sm font-semibold ml-3 mt-1">Install App</p>
            </button>
        </div>
        <div class="relative mt-3 w-full h-full">
            <div>
                <i
                    class="material-icons text-white absolute right-0 z-10 bg-black rounded-full opacity-0 hover:opacity-100">keyboard_arrow_down</i>
                <img src="./assets/img6.jpeg" class="max-w-full max-h-full absolute right-0" />
            </div>
        </div>
    </div>
</template>
<script setup>
import { ref } from "vue";

const albums = ref([
    { name: "drive" },
    { name: "zhu" },
    { name: "All new Indie" },
    { name: "Mellow" },
    { name: "Classic Road Trip Songs" },
    { name: "Lana Del Rey Radio" },
]);
</script>