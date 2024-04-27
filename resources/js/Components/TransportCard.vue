<script setup>
import { router } from '@inertiajs/vue3'


/* defineProps({
  titleTransport: String,
  transporter:String,
  transporterStatus: String,
  delayTransport: String,
}), */

  function handleClick() {
    router.visit('/details',); // Replace '/new-page' with your actual route
  }

</script>

<template>
    <div class="bg-white my-4 overflow-hidden shadow-sm rounded-lg" @click="handleClick">
        <div class="relative ">
        <p class="absolute top-1 right-1 p-2 rounded-lg bg-yellow-400 text-white font-semibold ">Pro</p><br>
     </div>
     <div>
        <p class=" m-2 text-3xl ">Trajet-xxx </p>
        <p class="m-2">Transporteur:   Thomas Pierre</p>
        <p class="flex flex-row text-xl items-center m-2"><svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
  <path stroke-linecap="round" stroke-linejoin="round" d="M6 12 3.269 3.125A59.769 59.769 0 0 1 21.485 12 59.768 59.768 0 0 1 3.27 20.875L5.999 12Zm0 0h7.5" />
</svg>
Départ: Cayenne 16h30</p>
<p class="flex flex-row text-xl items-center m-2"><svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
  <path stroke-linecap="round" stroke-linejoin="round" d="M6 12 3.269 3.125A59.769 59.769 0 0 1 21.485 12 59.768 59.768 0 0 1 3.27 20.875L5.999 12Zm0 0h7.5" />
</svg>
Arrivée: Saint-Georges 17h30</p>
     </div>

    </div>
</template>