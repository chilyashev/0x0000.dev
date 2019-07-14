<!--suppress HtmlUnknownTag -->
<template>
    <v-content>
        <v-container>
            <h1>About</h1>
        </v-container>
        <v-container>
            <p>Hi there,</p>

            <p>My name is Mihail Chilyashev and I spend most of my days writing software and solving the problems this
                creates.</p>
            <p></p>

            <v-btn to="projects" flat>
                Projects
            </v-btn>
        </v-container>
    </v-content>
</template>

<script>

    export default {
        layout: 'game',
        components: {},
        data() {
            return {
                host: 'kernelshocked'
            }
        }
    }
</script>


<style>
</style>
