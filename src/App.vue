<script setup lang="ts">
import {reactive, ref} from "vue";

type MediaType = {
  value: string,
  name: string,
};
const url = ref<string>('')
const selectedMediaType = ref<string>('audio')
const isLoading = ref(false);
const mediaTypes = reactive<MediaType[]>([
  {name: '.MP4', value: 'video'},
  {name: '.MP3', value: 'audio'},
])
const submitForm = () => void {
  /*submit form*/
}
</script>

<template>
  <div class="flex justify-center items-center w-full h-screen antialiased  bg-slate-900">
    <div class="w-full max-w-screen-md lg:mx-auto mx-8">
      <form class="flex flex-col items-center space-y-4 border bg-slate-300 p-4 bg-gray rounded-2xl shadow-xl" @submit.prevent="submitForm">
        <div class="flex w-full space-x-2">
          <input name="url"
                 v-model="url"
                 :disabled="isLoading"
                 type="search"
                 class="px-6 py-3 w-2/3 disabled:cursor-not-allowed rounded-lg text-black " placeholder="https:me.com/me.mp4"/>
          <select class="px-6 py-3 w-1/3 bg-white disabled:cursor-not-allowed rounded-lg text-black " v-model="selectedMediaType">
            <option v-for="mediaType in mediaTypes" :key="mediaType.value" :value="mediaType.value">
              {{ mediaType.name }}
            </option>
          </select>
        </div>
        <div class="flex w-full space-x-4">
          <button type="submit"
                  :disabled="isLoading"
                  class="text-white w-full focus:ring-4 font-medium rounded-lg
                 text-sm px-5 py-3 me-2 bg-blue-600 hover:bg-blue-700
                 focus:outline-none focus:ring-white disabled:opacity-45 disabled:cursor-not-allowed"
          >{{isLoading ? 'Loading...':'Start'}}</button>
        </div>

      </form>
    </div>
  </div>
</template>
