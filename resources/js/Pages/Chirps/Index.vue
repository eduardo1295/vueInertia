<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, Link, useForm, usePage } from '@inertiajs/vue3';
import PrimaryButton from "@/Components/PrimaryButton.vue";
import { ref } from 'vue';
import axios from 'axios';
import InputError from '@/Components/InputError.vue';
import ChirpItem from '@/Components/ChirpItem.vue';
import ChirpForm from '@/Components/ChirpForm.vue';

defineProps(['chirps'])



</script>

<template>
    <Head title="Dashboard" />

    <AuthenticatedLayout>

        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 dark:text-gray-200 leading-tight">{{ title }}</h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white dark:bg-gray-800 overflow-hidden shadow-sm sm:rounded-lg">
                    <div class="p-6 text-gray-900 dark:text-gray-100">
                       <!-- Form -->
                       <ChirpForm/>
                    </div>
                </div>
                <div class="">
                    <ChirpItem v-for="chirp in chirps" :key="`chirps-${chirp.id}`" :chirp="chirp"
                    />
                    
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
