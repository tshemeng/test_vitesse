<script setup lang="ts">
import { useHead } from '@vueuse/head'
import { Client } from 'rpc-websockets/build-ts/index.browser'

// https://github.com/vueuse/head
// you can use this to manipulate the document head in any components,
// they will be renedered correctly in the html results with vite-ssg
useHead({
  title: 'Vitesse',
  meta: [
    { name: 'description', content: 'Opinionated Vite Starter Template' },
  ],
})

const rpcLog = new Client(`ws://localhost:3090/ws/rpc_log`, { autoconnect: true, reconnect: true, reconnect_interval: 1000, max_reconnects: 20 })

rpcLog.on('message', (message:string)=>{
  console.log(message)
})

</script>

<template>
  <router-view />
</template>
