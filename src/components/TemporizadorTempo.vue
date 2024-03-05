<template>
    <div class="is-flex is-align-itens-center is-justify-content-space-between">
        <CronometroTempo :tempo-em-segundos="tempoEmSegundos" />
        <BotaoCLick @clicado="iniciar" icone="fas fa-play" texto="play" :desabilitado="cronometroRodando"/> 
        <BotaoCLick @clicado="finalizar" icone="fas fa-stop" texto="stop" :desabilitado="!cronometroRodando" />
    </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
import CronometroTempo from './CronometroTempo.vue';
import BotaoCLick from './BotaoCLick.vue';
export default defineComponent({
    name: 'TemporizadorTempo',
    emits: ['aoTemporizadorFinalizado'],
    components:{
    CronometroTempo,
    BotaoCLick
},
    data() {
        return {
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroRodando: false
        };
    },
    methods: {
        iniciar() {
            this.cronometroRodando = true;
            this.cronometro = setInterval(() => {
                this.tempoEmSegundos += 1;
                console.log('incrementado o contador');
            }, 1000);
            console.log('iniciando');
        },
        finalizar() {
            this.cronometroRodando = false
            clearInterval(this.cronometro);
            this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos);
            this.tempoEmSegundos = 0
            
            
        }
    },
})
</script>