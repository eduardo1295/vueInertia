<script setup>
defineProps({
    chirp: Object,
})
</script>

<template>
    <div class="">
        {{ chirp.created_at }} <br>
    
    {{ chirp.message }} <br>
    </div>
    
</template>