<script setup>
    const props = defineProps(['inputValorA', 'inputValorB', 'trocarFiltro']);
</script>
<template>
    <form class="p-5">
        <div class="row">
            <div class="col-md-4">
                <input @keyup="props.inputValorA" type="number"
                    placeholder="Digite o valor ''A'' " class="form-control" required>
            </div>
            <div class="col-md-4">
                <input @keyup="props.inputValorB" type="number"
                    placeholder="Digite o valor ''B'' " class="form-control" required>
            </div>
            <div class="col-md-4">
                <select @change="props.trocarFiltro" class="form-control">
                    <option value="soma">Soma</option>
                    <option value="subtracao">Subtração</option>
                    <option value="multiplicacao">Multiplicação</option>
                    <option value="divisao">Divisão</option>
                </select>
            </div>
        </div>
    </form>
</template>