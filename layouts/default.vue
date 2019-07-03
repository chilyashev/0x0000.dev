<!--suppress HtmlUnknownTag -->
<template>
  <v-app :dark="dark">
    <v-container grid-list-md>
      <v-layout row>
        <v-flex xs12>
          <v-toolbar>
            <v-toolbar-side-icon to="/">
              <v-img src="images/logo.png"></v-img>
            </v-toolbar-side-icon>
            <v-toolbar-title>Mihail Chilyashev</v-toolbar-title>
            <v-spacer></v-spacer>
            <v-toolbar-items class="hidden-sm-and-down">
              <v-btn v-for="(link, i) in links" :key="`menu${i}`" :to="link.to" flat>{{ link.title }}</v-btn>
              <v-btn flat @click="dark = !dark">
                <v-icon>invert_colors</v-icon>
              </v-btn>

            </v-toolbar-items>
          </v-toolbar>
        </v-flex>
      </v-layout>

      <v-layout row wrap>
        <v-flex xs12>
          <nuxt/>
        </v-flex>
      </v-layout>
    </v-container>


  </v-app>
</template>

<script>
  export default {
    data() {
      return {
        clipped: false,
        drawer: false,
        fixed: false,
        dark: false,
        links: [
          {
            title: "Home",
            to: "/"
          },
          {
            title: "Projects",
            to: "projects"
          },
          {
            title: "About",
            to: "about"
          },
        ],
        miniVariant: false,
        right: true,
        rightDrawer: false,
        title: 'Access violation at 0x00000000'
      }
    },
    head() {
      return {
        title: this.title,
        meta: [
          // hid is used as unique identifier. Do not use `vmid` for it as it will not work
          {hid: 'description', name: 'description', content: 'A personal website'}
        ]
      }
    }
  }
</script>

<style>
</style>
