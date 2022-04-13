<template>       
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model="descricao">
            </div>

            <div class="column">
                <div class="is-flex is-align-items-center is-justify-content-space-between">
                    <TemporizadorComponent @aoTemporarizadorFinalizado="finalizarTarefa"/>
                </div>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
    import {defineComponent} from 'vue';
    import TemporizadorComponent from './TemporizadorComponent.vue';
    

    export default defineComponent({
        name: 'FormularioPrincipal',
        data(){
            return {
                descricao: ''
            }
        },
        components: {
            TemporizadorComponent
        },
        methods: {
            finalizarTarefa(tempoDecorrido: number) :void
            {
                console.log("Tempo da Tarefa: " + tempoDecorrido); 
                console.log(`Descrição da Tarefa: ${this.descricao}`);
                this.descricao = '';
            }
        },
        watch: {
            'descricao': function(valorAtual, valorAntigo){
                console.log(`Descrição Atual: ${valorAtual} | Descrição Antiga: ${valorAntigo}`);
            }
        }
    });
</script>