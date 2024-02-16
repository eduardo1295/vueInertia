<script setup>
import Dropdown from '@/Components/Dropdown.vue';
import DropdownLinkButton from '@/Components/DropdownLinkButton.vue';
import DropdownLink from '@/Components/DropdownLink.vue';
import ChirpForm from '@/Components/ChirpForm.vue';
import {ref} from 'vue';
defineProps({
    chirp: Object,
})
const editing = ref(false);
</script>



<template>
    <div class="">
        
    
    <small class="ml-2 text-sm text-gray-600 dark:text-gray-400">
        {{  chirp.created_at }}
    </small>
    <small v-if="chirp.edited" class="text-sm text-gray-600 dark:text-gray-400">
        &middot; edited
    </small>
    <ChirpForm name="" id="" v-if="editing" :chirp="chirp" @cancel=" editing = false;" class="mt-4"/>
    <p v-else class="mt-4 text-lg text-gray-900 dark:text-gray-100">
        {{ chirp.message }}
    </p>
    <br>
    </div>
    
    <Dropdown>
        <template #trigger>Abir</template>
        <template #content>
            <DropdownLinkButton @click="editing = true; ">Edit</DropdownLinkButton>
            <DropdownLink 
            as="button" 
            :href="route('chirps.destroy',chirp.id)" 
            method="delete"
            :preserve-state="false"
            >Delete</DropdownLink>
            
        </template>
    </Dropdown>
</template>