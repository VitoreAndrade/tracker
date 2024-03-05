<template>
  <main class="columns is-gapless is-multiline" :class="{'modo-escuro':modoEscuroAtivo}">
    <div class="column is-one-quarter">
      <BarraLateral  @aoTemaAlterado="trocarTema"/>
    </div>
     <div class="column is-three-quarter conteudo">
      <FormularioEs @aoSalvarTarefa="salvarTarefa"/>
     
     <div class="lista">
      <TarefaFeita v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
      <BoxLista v-if="listaVazia">
        Você não está muito produtivo hoje :(
     </BoxLista>
     </div>
 
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormularioEs from './components/FormularioEs.vue';
import TarefaFeita from './components/TarefaFeita.vue';
import type ITarefa from '../src/Interface/ITarefa'
import BoxLista from './components/BoxLista.vue';
export default defineComponent({
    name: 'App',
    components: { BarraLateral, FormularioEs, TarefaFeita, BoxLista },
    data(){
      return{
        tarefas: [] as ITarefa [],
        modoEscuroAtivo: false
      }
    },
    computed:{
      listaVazia ():Boolean{
        return this.tarefas.length === 0
      }
    },
    methods:{
      salvarTarefa (tarefa: ITarefa){
        this.tarefas.push(tarefa)
      },
      trocarTema(modoEscuroAtivo: boolean){
        this.modoEscuroAtivo = modoEscuroAtivo
      }
    }

});
</script>

<style>
.lista{
  padding: 1.25rem;
}
main{
  --bg-primario:#ffffff;
  --texto-primario:#000000;
}
main.modo-escuro{
  --bg-primario:#2b2d42;
  --texto-primario:#ffffff;
  
}

.conteudo{
  background-color: var(--bg-primario);
}
</style>
