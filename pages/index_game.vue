<!--suppress HtmlUnknownTag -->
<template>
    <v-content>
        <v-container>
            <h1>About</h1>
        </v-container>
        <v-container>
            <p>Hi there,</p>

            <CanvasProvider style="width: 100%; height: 600px;">
                <player :width="200" :height="800"/>
            </CanvasProvider>
            <v-btn to="projects" flat>
                Projects
            </v-btn>
        </v-container>
    </v-content>
</template>

<script>
    import CanvasProvider from '../components/game/CanvasProvider';
    import Box from '../components/game/box';
    import Player from "../components/game/player";

    export default {
        layout: 'game',
        components: {Player, CanvasProvider, Box},
        data() {
            return {
                host: 'kernelshocked',
                playerX: 0,
            }
        },
        methods: {
            handleInput(event) {
                //console.log(event)
            }
        },
        mounted() {
            window.addEventListener('keydown', this.handleInput);
        },
        beforeDestroy() {
            window.removeEventListener('keydown', this.handleInput);
        },
    }
</script>


<style>
</style>
