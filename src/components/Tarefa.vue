<template>
    <Box>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao || 'Tarefa sem descrição' }}
            </div>
            <div class="column">
                <Cronometro :tempoEmSegundos="tarefa.duracaoEmSegundos" />
            </div>
        </div>
    </Box>
</template>

<script lang="ts">
import ITarefa from '@/interfaces/ITarefa';
import Cronometro from './Cronometro.vue';
import { PropType, defineComponent } from 'vue';
import Box from './Box.vue'
export default defineComponent({
    // eslint-disable-next-line vue/multi-word-component-names
    name:'Tarefa',
    components:{Cronometro,Box},
    props:{tarefa:{type:Object as PropType<ITarefa>, required:true}}
})
</script>

<style scoped>


</style>