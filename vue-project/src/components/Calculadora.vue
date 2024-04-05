<script setup>
import { reactive } from 'vue';


const estado = reactive({
    primeiroNumero: '',
    segundoNumero: '',
    operacoes: {
        soma: (a, b) => a + b,
        subtracao: (a, b) => a - b,
        multiplicacao: (a, b) => a * b,
        divisao: (a, b) => (b !== 0 ? a / b : 'Divisão por zero'),
    },
    resultado: 0,
});

const calcularResultado = () => {
    const { primeiroNumero, segundoNumero, operacaoMatematica } = estado;
    estado.resultado = estado.operacoes[operacaoMatematica](parseFloat(primeiroNumero), parseFloat(segundoNumero));
};
</script>

<template>

    <div class="container">
        <h1>Calculadora Aritmética Vue JS</h1>
        <input type="number" v-model="estado.primeiroNumero" @input="calcularResultado" />
        <input type="number" v-model="estado.segundoNumero" @input="calcularResultado" />
        <select v-model="estado.operacaoMatematica" @change="calcularResultado">
            <option value="soma">Soma</option>
            <option value="subtracao">Subtração</option>
            <option value="multiplicacao">Multiplicação</option>
            <option value="divisao">Divisão</option>
        </select>

        <p>Resultado: {{ estado.resultado }}</p>
    </div>

</template>

<style scoped>
h1 {
    font-size: 22px;
    text-align: center;
}

.container {
    margin: 100px 0px;
}

input,
select {
    display: block;
    width: 200px;
    margin: 10px auto;
    padding: 5px;
    border: none;
    outline: none;
    border-radius: 5px;
}

p {
    text-align: center;
}
</style>
