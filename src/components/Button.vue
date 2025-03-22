<script setup>
    const props = defineProps({
        operador: String
    })

</script>

<template>
    <button 
    type="button"
    class="rounded-full h-10 w-10 bg-fuchsia-700 font-bold mb-5 hover:outline-none hover:ring-2 hover:ring-offset-2 hover:ring-fuchsia-700 text-white text-2xl"
    @click="$emit('fn')"
    >{{operador}}</button>

</template>