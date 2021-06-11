<!-- 社交 -->

<template>
    <div class="social" :style="{'font-size': size + 'em'}">
        <!-- github -->
        <a :style="{color: color}" :href="social['github'] || 'https://github.com/exchar'" target="_blank"><a-icon type="github" /></a>
        <!-- gitee -->
        <a :style="{color: color}" :href="social['gitlab'] || 'https://gitee.com/exchar'" target="_blank"><a-icon type="gitlab" /></a>
    </div>
</template>

<script lang="ts">
    import {Component, Vue} from 'vue-property-decorator';
    import {mapGetters} from 'vuex';

    @Component({
        components: {
        },
        props: {
            color: String,
            size: Number,
        },
        computed: {
            ...mapGetters(['social']),
        },
    })
    export default class Social extends Vue {
    }
</script>

<style scoped lang="scss">
    .social {
        &>* {
            margin: 0.5em;
        }
    }
</style>

