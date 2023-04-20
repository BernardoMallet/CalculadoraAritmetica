<script setup>
import { reactive } from 'vue';

const operadorAritmetico = reactive({
    num1: 0,
    num2: 0,
    filtro: 'Soma'
})


const calcularResultado = () => {
    const { num1, num2, filtro } = operadorAritmetico;

    switch (filtro) {
        case 'Soma':
            return num1 + num2;
        case 'Subtração':
            return num1 - num2;
        case 'Multiplicação':
            return num1 * num2;
        case 'Divisão':
            return num1 / num2;
    }
}



</script>

<template>
    <form class="p-5">
        <div class="row">
            <div class="col">
                <input type="number" placeholder="Primeiro valor" class="form-control w-25" 
                    @change="evento => operadorAritmetico.num1 = parseInt(evento.target.value)" />
            </div>
        </div>
    <div class="row mt-2">
        <div class="col">
            <input type="number" placeholder="Segundo valor" class="form-control w-25" 
                @change="evento => operadorAritmetico.num2 = parseInt(evento.target.value)" />
        </div>
    </div>
    <select @change="evento => operadorAritmetico.filtro = evento.target.value" class="form-control w-25 mt-2">
        <option value="Soma">Soma</option>
        <option value="Subtração" >Subtração</option>
        <option value="Multiplicação">Multiplicação</option>
        <option value="Divisão" >Divisão</option>
    </select>
    <div class="row mt-2">
        <h4>
            Resultado: <span class="text-success">{{ calcularResultado() }}</span>
        </h4>
    </div>
    </form>
</template>
