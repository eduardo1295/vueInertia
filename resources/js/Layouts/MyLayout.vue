<template>
    <header>
        <nav>NAV</nav>
        <div v-if="$slots.title" class="br-green-200">
            <slot name="title" />
        </div>
    </header>
    <div class="bg-gray-200">
        <slot/>
    </div>
</template>
