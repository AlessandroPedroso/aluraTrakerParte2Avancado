<template>
 <div class="box has-text-weight-bold" :style="estilos">
    <slot></slot>
 </div>
</template>
 
<script lanf="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    // eslint-disable-next-line vue/multi-word-component-names
    name:"Box",
    data(){
        return{
            estilos:{
                // background: '#FAF0CA'
                //backgroundColor: '#FAF0CA'
                'background-color': '#FAF0CA'
            }
        }
    }
})
</script>

<!-- <style scoped>
.box{
    background: #FAF0CA;
}
</style> -->