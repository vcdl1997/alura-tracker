<template lang="">
    <section>
        <strong>
            {{tempoDecorrido}}
        </strong>
    </section>
</template>

<script lang="ts">
    import {defineComponent} from 'vue';
    export default defineComponent({
        name: 'CronometroTarefas',
        props: { //propriedades herdadas do componente pai
            segundos: {
                type: Number,
                default: 0
            }
        },
        computed: {
            tempoDecorrido () :string
            {
                return new Date(this.segundos * 1000).toISOString().substr(11,8)
            }
        }
    });

</script>