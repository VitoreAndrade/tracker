<template>
    <button class="button" @click="clicado" :disabled="desabilitado">
        <span class="icon">
            <i class="icone"></i>
        </span>
        <span>
            {{texto}}
        </span>
    </button>
</template>
<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name:'BotaoClick',
    emits:['clicado'],
    props: {
        desabilitado:{
            type: Boolean
        },
        icone:{
            type: String
        },
        texto:{
            type: String
        }
    },
    methods:{
        clicado(){
            this.$emit('clicado')
        }
    }
})


</script>