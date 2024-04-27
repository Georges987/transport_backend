<script setup>
import { Head, useForm } from '@inertiajs/vue3';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
</script>

<template>
     <Head title="details" />
 <div>
   
    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-[#20FF5E] leading-tight">Détail du trajet</h2>
        </template>

        <div class="mt-8 text-lg">
            <p class="flex flex-row m-2 items-center justify-normal ">
<span class="font-semibold mr-2">Départ:</span> Cayenne 16h30</p>
<p class="flex flex-row m-2 items-center  ">
<span class="font-semibold mr-2">Arrivée:</span> Saint-Georges 17h30</p>
<p class="flex flex-row m-2 items-center">
<span class="font-semibold mr-2">Nombres de places disponibles:</span> 20</p>
<p class="flex flex-row m-2 items-center">
<span class="font-semibold mr-2">Bagages possibles:</span> 1</p>
<div class="flex flex-row items-center m-2 gap-3">
<p class="font-semibold">Prix final:</p>
<p class="font-semibold text-2xl text-[#20FF5E] ml-2">24 euros</p>
</div>
<p class="font-semibold m-2">Arrêt possible en cours de route:</p>
   <div class="ml-6">
    <ul >
    <li>Macouria: +10 euros</li>
    <li>Mana: +15 euros</li>
   </ul>
   </div>
  <p ><span class="font-semibold m-2">J'ai des gilets de sauvetage pour vous:</span>Oui</p>
   <div class=" mt-4 flex flex-row justify-center">
    <PrimaryButton class="">
                            Valider votre présence
                        </PrimaryButton>
   </div>
        </div>
    </AuthenticatedLayout>
 </div>
</template>