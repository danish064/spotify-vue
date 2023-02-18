<template>
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
</template>
<script setup>
import { ref } from "vue";
</script>