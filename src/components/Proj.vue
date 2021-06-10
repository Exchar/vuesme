<template>
    <div class="content" id="proj">
        <ModuleHeader :title="proj.header.title" :sub-title="proj.header.subtitle"/>
        <a-timeline>
            <a-timeline-item data-aos="fade-in" v-for="card in proj.cards" v-bind:key="card.title + card.subtitle">
                <a-card class="proj-card" :bordered="true" style="width: 100%">
                    <template slot="title">
                        <h1 class="title">{{card.title}}</h1>
                        <span v-if="!!card.subtitle" class="sub-title">{{card.subtitle}}</span>
                    </template>
                    <p style="color:grey;font-size:0.8em">{{card.desc}}</p>
                    <a :href="card.url">
                    点我预览
                    </a>
                </a-card>
            </a-timeline-item>
        </a-timeline>
    </div>
</template>

<script lang="ts">
    import {Component, Vue} from 'vue-property-decorator';
    import ModuleHeader from '@/components/module/ModuleHeader.vue';
    import {Module} from '@/api/user_interface';
    // tslint:disable-next-line:no-var-requires
    import VueMarkdown from 'vue-markdown';

    @Component({
        components: {
            ModuleHeader,
            VueMarkdown,
        },
        computed: {
            proj(): Module {
                return this.$store.getters.getModule('proj');
            },
        },
    })
    export default class About extends Vue {
    }
</script>

<style scoped lang="scss">
    @import '../styles/variable';

    .proj-card {
        .title {
            width: 100%;
            font-size: 1rem;
            overflow: scroll;
            margin: 0;
        }

        .sub-title {
            width: 100%;
            font-size: .5rem;
            display: block;
            margin-top: .5rem;
        }
    }
</style>
