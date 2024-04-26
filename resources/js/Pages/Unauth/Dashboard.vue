<script setup>
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, useForm } from '@inertiajs/vue3';

const form = useForm({
    search: ''
});
</script>

<template>
    <Head title="Dashboard" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">Dashboard</h2>
        </template>

        <div class="py-12 mx-6">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white my-4 overflow-hidden shadow-sm sm:rounded-lg">
                    <form @submit.prevent="submit" class="flex p-6 text-gray-900">
                        <TextInput id="search" type="search" placeholder="Rechercher un transporteur" class="mt-1 block w-full" required autofocus autocomplete="username" />
                        <PrimaryButton class="ms-4" :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                            Rechercher
                        </PrimaryButton>
                    </form>
                </div>

                <div class="bg-white my-4 overflow-hidden shadow-sm sm:rounded-lg">
                    <div class="flex flex-col p-6 text-gray-900">
                        <div class="font-bold text-3xl my-4">
                            Trajets disponibles
                        </div>

                        <div>
                            Liste des travaux disponibles
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
