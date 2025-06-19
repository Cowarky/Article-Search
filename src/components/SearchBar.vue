<template>
    <div class="flex-row flex p-2 shadow-gray-800 shadow-md/10">
        <input v-model="searchedTerm" @keyup="emite('search', searchedTerm)" type="text" class="w-full border-2 border-amber-100 shadow-gray-800 shadow-md/10 flex-1">
        <div class="content-center">
          <img @click="emite('search', searchedTerm)" class="cursor-pointer" src="https://img.icons8.com/?size=20&id=132&format=png&color=000000" alt="">
        </div>
      </div>
      <div class="w-full h-2">
      <p class="text-xs my-2">
        <b>{{ props.count }}</b> found
      </p>
    </div>
</template>
<script setup lang="ts">
import { ref } from 'vue';

const props = defineProps(['count'])
const emite = defineEmits(['search'])
const searchedTerm = ref()

</script>