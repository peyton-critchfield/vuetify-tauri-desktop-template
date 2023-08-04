<template>
  <div class="container">
    <div style="display: flex">
      <v-img
      :src="require('../assets/logo.svg')"
      class="my-3"
      contain
      height="200"
      />
      <v-img
      :src="require('../assets/logo.png')"
      class="my-3"
      contain
      height="200"
      />
    </div>
    <div style="display: flex">
      <v-img
      :src="require('../assets/tauri.png')"
      class="my-3"
      contain
      height="200"
      />
      <v-img
      :src="require('../assets/rust.png')"
      class="my-3"
      contain
      height="200"
      />
    </div>
    <div v-if="greeting" style="color:white;text-align: center;">
      {{ greeting }}
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { invoke } from '@tauri-apps/api/tauri'

const greeting = ref("");

const init = async () => {
    greeting.value = await invoke("greeting");
    console.log(greeting.value)
}
init()

</script>

<style>
.container {
  background-color: black;
  width: 100vw;
  height: 100vh;
}
</style>