<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para a criação de uma nova tarefa">
                <input type="text" class="input" v-model="descricao" placeholder="Qual tarefa você deseja iniciar?">
            </div>
            <div class="column">
                
                <Temporizador @ao-temporizador-finalizado="finalizarTarefa"/>

            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Temporizador from './Temporizador.vue';
import ITarefa from '@/interfaces/ITarefa'

export default defineComponent({
    // eslint-disable-next-line vue/multi-word-component-names
    name: 'Formulario',

    components:{Temporizador},
    data(){
        return{
            descricao: ''
        }
    },
    emits: ['aoSalvarTarefa'],
    methods:{
        finalizarTarefa(tempoDecorrido: number):void{
            console.log(`tempo decorrido da tarefa decorrido: ${tempoDecorrido}`)
            console.log(`descricao da tarefa informada: ${this.descricao}`)
            
            const ObjetoTarefa:ITarefa = {
                duracaoEmSegundos:tempoDecorrido,
                descricao: this.descricao
            }

            this.$emit('aoSalvarTarefa',ObjetoTarefa)
            this.descricao = ''
        }
    }

})
</script>

<style>
.formulario{
    color: var(--texto-primario);
    background-color: var(--bg-primario);
}

</style>