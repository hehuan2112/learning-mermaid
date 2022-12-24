<script setup>
import { ref, onUpdated } from 'vue';
import MFC from './components/MFC.vue';

const ref_MFC = ref()

let chart_code = ref(`graph TD
A[Christmas] -->|Get money| B(Go shopping)
B --> C{Let me think}
C -->|One| D[Laptop]
C -->|Two| E[iPhone]
C -->|Three| N0[fa:fa-car Car]
`);

function update_MFC() {
  ref_MFC.value.render_mermaid();
}
</script>

<template>
  <div style="display: flex; flex-direction: row;">
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>

    <textarea name="" id="" cols="30" rows="10" v-model="chart_code"></textarea>

    <div id="MFC_box">
      <button @click="update_MFC">Update</button>
      <MFC ref="ref_MFC" 
        :chart_code="chart_code">
      </MFC>
    </div>
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
