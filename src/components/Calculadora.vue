<script setup>
import { ref, computed } from 'vue';

const primeiroNumero = ref('');
const segundoNumero = ref('');
const operacaoMatematica = ref('soma');

const resultado = computed(() => {
    const num1 = parseFloat(primeiroNumero.value);
    const num2 = parseFloat(segundoNumero.value);

    if (isNaN(num1) || isNaN(num2)) return '';

    switch (operacaoMatematica.value) {
        case 'soma':
            return num1 + num2;
        case 'subtracao':
            return num1 - num2;
        case 'multiplicacao':
            return num1 * num2;
        case 'divisao':
            return num2 !== 0 ? num1 / num2 : 'Divisão por zero';
        default:
            return '';
    }
});
</script>

<template>
    <div class="container">
        <h1 class="fnt">Calculadora Vue</h1>

        <input type="number" v-model="primeiroNumero" placeholder="Primeiro Número" />
        <input type="number" v-model="segundoNumero" placeholder="Segundo Número" />

        <select v-model="operacaoMatematica">
            <option value="soma">Somar</option>
            <option value="subtracao">Subtrair</option>
            <option value="multiplicacao">Multiplicar</option>
            <option value="divisao">Dividir</option>
        </select>

        <p>Resultado: {{ resultado }}</p>
    </div>
</template>

<style scoped>
.container {
    width: 340px;
    margin: 0 auto;
    padding: 60px;
    background-color: #e2e2e2;
    border-radius: 10px;
    margin-top: 100px;
    text-align: center;
    font-size: 20px;
}

.fnt {
    font-size: 2em;
}

input {
    margin: 15px 0;
    padding: 10px;
    width: 300px;
    border: 1px solid #ccc;
    border-radius: 3px;
}

select {
    margin: 10px;
    padding: 10px;
    width: 150px;
    border: 1px solid black;
    border-radius: 3px;
}

</style>
