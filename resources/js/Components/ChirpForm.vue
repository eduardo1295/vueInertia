<script setup>
import { Head, Link, useForm, usePage } from '@inertiajs/vue3';
import PrimaryButton from "@/Components/PrimaryButton.vue";
import SecondaryButton from "@/Components/SecondaryButton.vue";
import InputError from '@/Components/InputError.vue';

const {chirp} = defineProps({
    chirp : Object
})

const form = useForm({
    message: chirp?.message
})

function update(chirp){
    form.patch(route('chirps.update',chirp),{
        onSuccess: () => {form.reset()},
        preserveState: false
    })
}

function submit(){
    if(chirp?.id){
        update(chirp.id)
        return
    }
    form.post(route('chirps.store'),{
        onSuccess: () => {form.reset()},
        preserveState: false
    })
}

</script>
<template>
    <form @submit.prevent="submit">
                        <textarea v-model="form.message" class="block w-full rounded-md border-gray-300 bg-white"></textarea>
                        <InputError :message="form.errors.message" ></InputError>
                        
                        
                        <PrimaryButton  :disabled="form.processing" class="mt-2">{{  form.processing ? 'Enviando..' : 'Chirps' }}</PrimaryButton>
                        <SecondaryButton v-if="chirp?.id" @click="$emit('cancel')"  class="ml-2"  > Cancel </SecondaryButton>
                       </form>
</template>