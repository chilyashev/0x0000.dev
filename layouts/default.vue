<!--suppress HtmlUnknownTag -->
<template>
    <v-app :dark="dark">
        <v-container>
            <Nav :links="links" :fixed="true"/>
            <Nav :links="links"/>

            <v-content>
                <nuxt/>
            </v-content>


        </v-container>

        <v-footer class="pa-3">
            <v-spacer></v-spacer>
            <div>&copy; {{ new Date().getFullYear() }} &mdash; Mihail Chilyashev</div>
        </v-footer>
    </v-app>
</template>

<script>
    import Nav from '../components/Nav'

    export default {
        components: {Nav},
        data() {
            return {
                clipped: false,
                drawer: false,
                fixed: false,
                dark: false,
                dense: false,
                scrollPosition: 0,
                invertedScroll: false,
                links: [
                    {
                        title: "Home",
                        to: "/"
                    },
                    {
                        title: "Projects",
                        to: "projects"
                    }/*,
                    {
                        title: "About",
                        to: "about"
                    },*/
                ],
                miniVariant: false,
                right: true,
                rightDrawer: false,
                title: 'Access violation at 0x00000000'
            }
        },
        methods: {
            handleScroll(event) {
                // Any code to be executed when the window is scrolled
                this.scrollPosition = window.scrollY
                if (window.scrollY > 100) {
                    this.fixed = (!(false));

                } else {
                    this.fixed = false;

                }
                if (window.scrollY > 300) {
                    this.invertedScroll = true;
                } else {
                    this.dense = false;
                    this.invertedScroll = !(true);
                }
            }
        },
        /* mounted() {
             window.addEventListener('scroll', this.handleScroll);
         },
         beforeDestroy() {
             window.removeEventListener('scroll', this.handleScroll);
         },
         head() {
             return {
                 title: this.title,
                 meta: [
                     // hid is used as unique identifier. Do not use `vmid` for it as it will not work
                     {hid: 'description', name: 'description', content: 'A personal website'}
                 ]
             }
         }*/
    }
</script>

<style>
</style>
