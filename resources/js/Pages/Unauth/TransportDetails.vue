<script setup>
import { ref } from 'vue';
import { Head, useForm } from '@inertiajs/vue3';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import Modal from '@/Components/Modal.vue';
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';

const isShowable = ref(false)
const secondIsShowable = ref(false)
const thirdIsShowable = ref(false)
const canPay = ref(false)
const isCloseable = ref(false)

function handlePay() {
    canPay.value = true
    isShowable.value = false
}

function canParticipate() {
    isShowable.value = false
    thirdIsShowable.value = true
}

function handleNotif() {
    secondIsShowable.value = false
    thirdIsShowable.value = false
}
</script>

<template>

    <Head title="details" />
    <div>

        <AuthenticatedLayout>
            <template #header>
                <h2 class="font-semibold text-xl text-green-700 leading-tight">Détail du trajet</h2>
            </template>

            <div class="mt-8 text-lg">
                <p class="flex flex-row m-2 items-center justify-normal ">
                    <span class="font-semibold mr-2">Départ:</span> Cayenne 16h30
                </p>
                <p class="flex flex-row m-2 items-center  ">
                    <span class="font-semibold mr-2">Arrivée:</span> Saint-Georges 17h30
                </p>
                <p class="flex flex-row m-2 items-center">
                    <span class="font-semibold mr-2">Nombres de places disponibles:</span> 20
                </p>
                <p class="flex flex-row m-2 items-center">
                    <span class="font-semibold mr-2">Bagages possibles:</span> 1
                </p>
                <div class="flex flex-row items-center m-2 gap-3">
                    <p class="font-semibold">Prix final:</p>
                    <p class="font-semibold text-2xl text-green-700 ml-2">24 euros</p>
                </div>
                <p class="font-semibold m-2">Arrêt possible en cours de route:</p>
                <div class="ml-6">
                    <ul>
                        <li>Macouria: +10 euros</li>
                        <li>Mana: +15 euros</li>
                    </ul>
                </div>
                <p><span class="font-semibold m-2">J'ai des gilets de sauvetage pour vous:</span>Oui</p>
                <div class=" mt-4 flex flex-row justify-center">
                    <PrimaryButton class="" @click="isShowable = !isShowable">
                        <p v-if="!canPay">Valider votre présence</p>
                        <p v-else>Validé!</p>
                    </PrimaryButton>
                </div>
            </div>
            <Modal :show="isShowable" :closeable="isCloseable">
                <div>
                    <PrimaryButton class="absolute top-0 right-0" @click="isShowable = !isShowable">
                        x
                    </PrimaryButton>
                </div>
                <p class="m-6">Pouvez vous payer en ligne?</p>
                <p></p>
                <div class="flex flex-row justify-end">
                    <button
                        class="bg-red-500 mx-1 inline-flex items-center px-4 py-2 border border-transparent rounded-md font-semibold text-xs text-white uppercase tracking-widest  focus:outline-none  transition ease-in-out duration-150"
                        @click="canParticipate
                        ">
                        Non
                    </button>
                    <PrimaryButton @click="handlePay">
                        Oui
                    </PrimaryButton>

                </div>
            </Modal>
            <Modal :show="thirdIsShowable" :closeable="isCloseable">
                <div>
                    <PrimaryButton class="absolute top-0 right-0" @click="thirdIsShowable = !thirdIsShowable">
                        x
                    </PrimaryButton>
                </div>
                <p class="m-6">Souhaitez vous quand même participer?</p>
                <p></p>
                <div class="flex flex-row justify-end">
                    <button
                        class="bg-red-500 mx-1 inline-flex items-center px-4 py-2 border border-transparent rounded-md font-semibold text-xs text-white uppercase tracking-widest  focus:outline-none  transition ease-in-out duration-150"
                        @click="thirdIsShowable = !thirdIsShowable">
                        Non
                    </button>
                    <PrimaryButton @click="secondIsShowable = !secondIsShowable">
                        Oui
                    </PrimaryButton>

                </div>
            </Modal>
            <Modal :show="secondIsShowable">
                <p class="m-6">Vous recevrez une notification sous peu</p>
                <p class="ml-4"><span class="underline">NB:</span> Ce moyen est moins fiable et fonctionne grâce à la
                    <span class="font-semibold">confiance mutuelle</span></p>
                <div class="flex flex-row justify-end">
                    <PrimaryButton @click="handleNotif">
                        OK
                    </PrimaryButton>
                </div>
            </Modal>
        </AuthenticatedLayout>
    </div>
</template>
