<script setup>
import { onBeforeMount, onMounted } from 'vue';
import { useInitParse, useInitPostHog, usePageId } from '../utils/utils.js'

import axios from 'axios'

onBeforeMount(async() =>{
  usePageId()
  await getParseId()
  await useInitParse()
})
onMounted(async() => {
  
})

useInitPostHog()
  
async function getParseId() {
  return new Promise((resolve, reject) => {
    const appId = import.meta.env.VITE_APP_ID;
    if (!appId) {
      reject(new Error('VITE_APP_ID manquant'));
      return;
    }
    localStorage.setItem('parse_app_id', appId);
    resolve(appId);
  });
}


  })
}
</script>
<template>
  <header class="text-center">
    <!-- Fixed navbar -->
    <img class="navLogo" />
  </header>
  <slot />
</template>
