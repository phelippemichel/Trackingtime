<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <CronometroTempo :tempoEmSegundos="tempoEmSegundos" />
        <button class="button" @click="iniciar" :disabled="cronometroFuncionando">
            <span class="icon">
                <i class="fas fa-play"></i>
            </span>
            <span>play</span>
        </button>
        <button class="button" @click="finalizar" :disabled="!cronometroFuncionando">
            <span class="icon">
                <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
        </button>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import CronometroTempo from './CronometroTempo.vue'

export default defineComponent({
    name: 'TemporizadorTarefas',
    emits: ['TemporizadorFinalizado'],
    components: {
        CronometroTempo
    },
    data() {
        return {
            tempoEmSegundos: 0,
            CronometroTempo: 0,
            cronometroFuncionando: false
        }
    },

    methods: {
        iniciar() {
            this.cronometroFuncionando = true
            this.CronometroTempo = setInterval(() => {
                this.tempoEmSegundos += 1
            }, 1000)
        },
        finalizar() {
            this.cronometroFuncionando = false
            clearInterval(this.CronometroTempo)
            this.$emit('TemporizadorFinalizado', this.tempoEmSegundos)
            this.tempoEmSegundos = 0
        }
    }
});

</script>