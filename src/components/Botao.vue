<template>
        <button class="button" @click="clicado" :disabled="desabilitando">
            <span class="icon">
                <i :class="icone"></i>
            </span>
            <span>{{ texto }}</span>
        </button>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    // eslint-disable-next-line vue/multi-word-component-names
    name:'Botao',
    emits:['clicando'],
    props:{
        desabilitando: {type: Boolean},
        icone: {type:String, required:true},
        texto: {type:String, required:true},

    },
    methods:{
        clicado():void{
            this.$emit('clicando');
        }
    }
})

</script>

<style scoped>
</style>