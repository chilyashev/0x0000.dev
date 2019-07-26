<template>
    <v-toolbar :inverted-scroll="fixed" :app="fixed" :fixed="fixed" :scroll-off-screen="fixed" :dark="dark">
        <v-toolbar-side-icon to="/">
            <v-img src="images/logo.png"></v-img>
        </v-toolbar-side-icon>
        <v-toolbar-title>
            <span class="grey--text">Mihail Chilyashev</span>
        </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-toolbar-items class="hidden-sm-and-down">
            <v-btn v-for="(link, i) in links" :key="`menu${i}`" :to="link.to" flat>{{ link.title }}
            </v-btn>
            <!--<v-btn flat @click="dark = !dark">
                <v-icon>invert_colors</v-icon>
            </v-btn>-->

        </v-toolbar-items>
    </v-toolbar>
</template>

<script>
    export default {
        name: "Nav",
        props: {
            links: {type: Array},
            fixed: {type: Boolean},
            dense: {type: Boolean, default: true},
        },
        data() {
            return {
                dark: false
            }
        }
    }
</script>

<style scoped>

</style>
