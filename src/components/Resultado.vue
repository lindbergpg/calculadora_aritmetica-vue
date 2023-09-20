<script setup>
    const props = defineProps(['nomeFuncao', 'resultado'])
</script>
<template>
    <div class="text-center">
        <h2 class="mb-4">Resultado</h2>
        <p class="fs-3">{{ props.nomeFuncao }} é igual a {{ props.resultado }}.</p>
    </div>
</template>