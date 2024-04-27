<script setup>
import { ref } from 'vue';
import { Head, useForm } from '@inertiajs/vue3';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import Modal from '@/Components/Modal.vue';
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue'

const validate = ref(true)
const userValidate = ref(true)

const isShowable = ref(false)
function inValidateUser() {
    validate.value = false
    isShowable.value = true
    userValidate.value = false
}

function ValidateUser() {
    validate.value = true
    isShowable.value = true
    userValidate.value = false
}
</script>

<template>

    <Head title="transporteur" />
    <div>

        <AuthenticatedLayout>
            <template #header>
                <h2 class="font-semibold text-xl text-green-700 leading-tight">Profil Transporteur</h2>
            </template>
            <div class="mt-4">
                <div class=" bg-white rounded-xl py-10">
                    <div class="flex flex-col justify-center">
                        <div class="flex flex-row justify-normal">
                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                                stroke="currentColor" class="w-20 h-20 mx-4 my-auto">
                                <path stroke-linecap="round" stroke-linejoin="round"
                                    d="M17.982 18.725A7.488 7.488 0 0 0 12 15.75a7.488 7.488 0 0 0-5.982 2.975m11.963 0a9 9 0 1 0-11.963 0m11.963 0A8.966 8.966 0 0 1 12 21a8.966 8.966 0 0 1-5.982-2.275M15 9.75a3 3 0 1 1-6 0 3 3 0 0 1 6 0Z" />
                            </svg>
                            <div>
                                <p class="font-semibold text-xl mt-4">Thomas Pierre</p>
                                <p>Transporteur</p>
                                <PrimaryButton class="my-4">
                                    Editer le Profil
                                </PrimaryButton>
                            </div>
                        </div>
                    </div>
                    <div>
                        <div class="border-2 bg-gray-200 m-2 client flex flex-row items-center justify-around">
                            <p class="text-lg font-semibold  ">Mes Trajets</p>
                            <PrimaryButton class="my-2">Proposer un trajet</PrimaryButton>
                        </div>
                        <div class="flex flex-row items-center justify-around">
                            <p class="font-semibold text-lg ">Trajet-xxx</p>
                            <div>
                                <PrimaryButton>Modifier</PrimaryButton>
                            </div>
                        </div>

                    </div>
                    <div>
                        <div class="border-2 bg-gray-200 m-2 client">
                            <p class="text-lg font-semibold  ">Clients à Valider</p>
                        </div>
                        <div class="flex flex-row items-center justify-around" v-show="userValidate">
                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                                stroke="currentColor" class="w-16 h-16 ml-4">
                                <path stroke-linecap="round" stroke-linejoin="round"
                                    d="M17.982 18.725A7.488 7.488 0 0 0 12 15.75a7.488 7.488 0 0 0-5.982 2.975m11.963 0a9 9 0 1 0-11.963 0m11.963 0A8.966 8.966 0 0 1 12 21a8.966 8.966 0 0 1-5.982-2.275M15 9.75a3 3 0 1 1-6 0 3 3 0 0 1 6 0Z" />
                            </svg>
                            <p class="font-semibold text-lg ">Thomas Pierre</p>
                            <div>
                                <button
                                    class="bg-red-500 hover:bg-red-600 mx-1 inline-flex items-center px-4 py-2 border border-transparent rounded-md font-semibold text-xs text-white uppercase tracking-widest  focus:outline-none  transition ease-in-out duration-150"
                                    @click="inValidateUser">
                                    Refuser
                                </button>
                                <PrimaryButton @click="ValidateUser">Valider</PrimaryButton>
                            </div>
                        </div>

                    </div>
                </div>
                <Modal :show="isShowable">
                    <p class="text-lg text-red-500 m-6" v-if="!validate">Client rejeté</p>
                    <p class="text-lg text-green-700 m-6" v-else>Client validé</p>
                    <div class="flex flex-row justify-end">
                        <PrimaryButton @click=" isShowable = !isShowable">
                            OK
                        </PrimaryButton>
                    </div>
                </Modal>
            </div>

        </AuthenticatedLayout>
    </div>
</template>

<style>
.client {
    --tw-bg-opacity: 1;
    background-color: rgb(229 231 235 / var(--tw-bg-opacity));
}

.text-red-500 {
    --tw-text-opacity: 1;
    color: rgb(239 68 68 / var(--tw-text-opacity));
}

.border-red-500 {
    border-width: 2px;
    --tw-border-opacity: 1;
    border-color: rgb(239 68 68 / var(--tw-border-opacity));
}
</style>
