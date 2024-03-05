
import CronometroTempo from './CronometroTempo.vue';
<template>
    <BoxLista>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao || 'Tarefa sem descrição' }}
            </div>
            <div class="column">
               <CronometroTempo :tempo-em-segundos="tarefa.duracaoEmSegundos" />
            </div>
        </div>
    </BoxLista>
</template>
<script lang="ts">
import {defineComponent, PropType } from 'vue';
import CronometroTempo from './CronometroTempo.vue';
import ITarefa from '@/Interface/ITarefa';
import BoxLista from './BoxLista.vue'


export default defineComponent({
    name:'TarefaFeita',
    components:{
    CronometroTempo,
    BoxLista
},
props:{
    tarefa:{
        type: Object as PropType<ITarefa>, 
            required:true
    }
}
})
</script>
