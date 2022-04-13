<template>
    <CronometroTarefas :segundos="segundos"/>

    <button class="button" @click="inicializar" :disabled="cronometroRodando">
        <span class="icon">
            <i class="fas fa-play"></i>
        </span>
        <span>
            play
        </span>
    </button>

    <button class="button" @click="finalizar" :disabled="!cronometroRodando">
        <span class="icon">
            <i class="fas fa-stop"></i>
        </span>
        <span>
            stop
        </span>
    </button>
</template>


<script lang="ts">
    import {defineComponent} from 'vue';
    import CronometroTarefas from './CronometroTarefas.vue';

    export default defineComponent({
        name: 'TemporizadorComponent',
        emits: [
            'aoTemporarizadorFinalizado'
        ],
        data(){
            return {
                cronometro: 0,
                segundos: 0,
                cronometroRodando: false,
                // minutos: 0,
                // horas: 0,
                // tempo: '00:00:00'
            }
        },
        components: {
            CronometroTarefas
        },
        methods: {
            inicializar() :void
            {
                this.cronometroRodando = true;
                this.cronometro = setInterval(()=>{
                    this.segundos = ++this.segundos;
                }, 1000);
            },
            finalizar() :void
            {
                clearInterval(this.cronometro);
                this.cronometroRodando = false;
                this.$emit('aoTemporarizadorFinalizado', this.segundos);
                this.segundos = 0;
            },
        },
    })
</script>