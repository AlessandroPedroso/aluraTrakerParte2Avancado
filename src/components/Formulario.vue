<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column is-5" role="form" aria-label="Formulário para a criação de uma nova tarefa">
                <input type="text" class="input" v-model="descricao" placeholder="Qual tarefa você deseja iniciar?">
            </div>
            <div class="column is-3">
                <div class="select">
                    <select v-model="idProjeto">
                        <option value="">Selecione o projeto</option>
                        <option :value="projeto.id" v-for="projeto in projetos" :key="projeto.id">
                            {{ projeto.nome }}
                        </option>
                    </select>
                </div>
            </div>
            <div class="column">

                <Temporizador @ao-temporizador-finalizado="finalizarTarefa" />

            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { computed, defineComponent } from 'vue';
import Temporizador from './Temporizador.vue';
import { useStore } from 'vuex';

import { key } from '@/store/index';
import ITarefa from '@/interfaces/ITarefa';

export default defineComponent({
    // eslint-disable-next-line vue/multi-word-component-names
    name: 'Formulario',
    components: { Temporizador },
    
    data() {
        return {
            descricao: '',
            idProjeto: ''
        }
    },
    emits: ['aoSalvarTarefa'],
    methods: {
        
        finalizarTarefa(tempoDecorrido: number): void {
            console.log(`tempo decorrido da tarefa decorrido: ${tempoDecorrido}`)
            console.log(`descricao da tarefa informada: ${this.descricao}`)

            const ObjetoTarefa = {
                duracaoEmSegundos: tempoDecorrido,
                descricao: this.descricao,
                projeto:this.projetos.find(proj=> proj.id == this.idProjeto)
            } as ITarefa

            this.$emit('aoSalvarTarefa', ObjetoTarefa)
            this.descricao = ''
        }
    },

    setup() {
        const store = useStore(key)
        return {
            projetos: computed(() => store.state.projetos)
        }
    }

})
</script>

<style>
.formulario {
    color: var(--texto-primario);
    background-color: var(--bg-primario);
}
</style>