<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';
import PrimaryButton from "@/Components/PrimaryButton.vue";
import { ref } from 'vue';
import axios from 'axios';
import InputError from '@/Components/InputError.vue';
defineProps(['title','subtitle'])



const form = useForm({
    message: ''
})

function submit(){
    form.post(route('chirps.store'),{
        onSuccess: () => {form.reset()},
    })
}
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
                       <form @submit.prevent="submit">
                        <textarea v-model="form.message" class="block w-full rounded-md border-gray-300 bg-white"></textarea>
                        <InputError :message="form.errors.message" ></InputError>
                        
                        
                        <PrimaryButton  :disabled="form.processing" class="mt-2">{{  form.processing ? 'Enviando..' : 'Chirps' }}</PrimaryButton>
                       </form>
                    </div>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
