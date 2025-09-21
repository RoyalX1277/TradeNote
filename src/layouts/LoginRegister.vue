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
    try {
      console.log("**GETTING APP ID (from env)");
      const appId = import.meta.env.VITE_PARSE_APP_ID;
      if (!appId) throw new Error("VITE_PARSE_APP_ID is missing");
      
      // Sauvegarde en localStorage comme avant
      localStorage.setItem('parse_app_id', appId);

      resolve(appId);
    } catch (error) {
      console.log(" --> Error getting app id " + error);
      reject(error);
    }
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
