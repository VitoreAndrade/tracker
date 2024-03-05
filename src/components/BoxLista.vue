<template>
<div class="box has-test-weight-bold" :style="estilos">
<slot></slot>
</div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
   name:'BoxLista' ,
   data (){
    return{
        estilos:{
            background: '#FAF0CA'
        }
    }
   }
})
</script>
