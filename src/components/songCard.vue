<template>
    <div class="absolute w-full h-full flex items-end justify-end p-8 opacity-0 hover:opacity-100">
        <div class="bg-green-500 rounded-full h-10 w-10 flex items-center justify-center">
            <i class="material-icons text-white text-2xl">play_arrow</i>
        </div>
    </div>
    <div class="bg-light w-full h-auto p-5 rounded-lg shadow-md">
        <img :src="song.src" class="h-auto shadow mb-2" />
        <h1 class="text-sm font-semibold text-white tracking-wide">
            {{ song.title }}
        </h1>
        <h2 class="text-xs text-white tracking-wide pb-5">
            {{ song.artists }}
        </h2>
    </div>
</template>
<script setup>
const props = defineProps({
    song: {
        type: Object,
        required: true,
    },
});
</script>
