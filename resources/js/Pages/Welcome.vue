<script setup>
import ApplicationLogo from '@/Components/ApplicationLogo.vue';
import { Head, Link } from '@inertiajs/vue3';

defineProps({
    canLogin: {
        type: Boolean
    },
    canRegister: {
        type: Boolean
    },
    laravelVersion: {
        type: String,
        required: true
    },
    phpVersion: {
        type: String,
        required: true
    }
});
</script>

<template>
    <Head title="Welcome" />

    <div>
        <div>
            <div v-if="canLogin" class="sm:fixed sm:top-0 sm:right-0 p-6 text-end">
                <Link
                    v-if="$page.props.auth.user"
                    :href="route('dashboard')"
                    class="font-semibold focus:outline focus:outline-2 focus:rounded-sm focus:outline-red-500"
                    >Dashboard</Link
                >

                <template v-else>
                    <Link
                        :href="route('login')"
                        class="font-semibold focus:outline focus:outline-2 focus:rounded-sm focus:outline-red-500"
                        >Se connecter</Link
                    >

                    <Link
                        v-if="canRegister"
                        :href="route('register')"
                        class="ms-4 font-semibold focus:outline focus:outline-2 focus:rounded-sm focus:outline-red-500"
                        >S'inscrire</Link
                    >
                </template>
            </div>
        </div>
        <div class="flex text-center flex-col justify-center h-screen">
            <ApplicationLogo class="h-1/4 font-thin"></ApplicationLogo>
            <div class="text-5xl font-bold">
                Transport
            </div>
        </div>
    </div>
</template>
