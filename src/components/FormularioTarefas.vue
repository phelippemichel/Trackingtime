<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário de novas tarefas">
                <input type="text" class="input" placeholder="Qual tarefa deseja iniciar?" v-model="descricao">
            </div>
            <div class="column">
                <TemporizadorTarefas @TemporizadorFinalizado="finalizarTarefa" />
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TemporizadorTarefas from './TemporizadorTarefas.vue'

export default defineComponent({
    name: 'FormularioTarefas',
    components: {
        TemporizadorTarefas
    },
    data() {
        return {
            descricao: ''
        }
    },
    methods: {
        finalizarTarefa(tempoDecorrido: number): void {
            console.log('tempo da tarefa', tempoDecorrido)
            console.log('descrição da tarefa', this.descricao)
            this.descricao = ''
        }
    }
});

</script>
