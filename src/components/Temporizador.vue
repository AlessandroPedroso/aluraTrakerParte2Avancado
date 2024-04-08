<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <cronometro :tempoEmSegundos="tempoEmSegundos" />
        <Botao @clicando="iniciar" icone="fas fa-play" texto="play" :desabilitando="cronometroRodando" />
        <Botao @clicando="finalizar" icone="fas fa-stop" texto="stop" :desabilitando="!cronometroRodando" />
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Cronometro from './Cronometro.vue'
import Botao from './Botao.vue'

export default defineComponent({
    // eslint-disable-next-line vue/multi-word-component-names
    name: 'Temporizador',
    emits:['aoTemporizadorFinalizado'],
    data(){
        return {
            tempoEmSegundos:0,
            cronometro:0,
            cronometroRodando: false
        }
    },
    components:{Cronometro,Botao},
    methods: {
        iniciar() {
            // começar a contagem
            // 1 seg = 1000 ms
            this.cronometroRodando = true;
            this.cronometro = setInterval(()=>{
                // console.log('incrementando o contador')
                this.tempoEmSegundos +=1
            },1000)
            
            // console.log('iniciando');
        },

        finalizar() {
            // console.log('finalizando');
            this.cronometroRodando = false;
            clearInterval(this.cronometro);
            // vai emit o evento com o valor do temporizador quando finalizar
            this.$emit('aoTemporizadorFinalizado',this.tempoEmSegundos);
            this.tempoEmSegundos = 0;
        }
    }
})
</script>

<style scoped>

</style>