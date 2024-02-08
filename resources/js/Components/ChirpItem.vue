<script setup>
import Dropdown from '@/Components/Dropdown.vue';
import DropdownLinkButton from '@/Components/DropdownLinkButton.vue';
import {ref} from 'vue';
defineProps({
    chirp: Object,
})
const editing = ref(false);
</script>



<template>
    <div class="">
        {{ chirp.created_at }} <br>
    <textarea name="" id="" v-if="editing" >{{ chirp.message }}</textarea>
    <p class="mt-4 text-lg text-gray-900 dark:text-gray-100">
        {{ chirp.message }}
    </p>
    <br>
    </div>
    
    <Dropdown>
        <template #trigger>Abir</template>
        <template #content>
            <DropdownLinkButton @click="editing = true;">Editar</DropdownLinkButton>
            <DropdownLinkButton @click="console.log('Eliminar')">Eliminar</DropdownLinkButton>
            
        </template>
    </Dropdown>
</template>