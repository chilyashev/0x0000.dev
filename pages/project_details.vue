<!--suppress HtmlUnknownTag -->
<template>
  <v-container>
    <v-layout row wrap>
      <v-flex xs12 md4 v-for="(project, i) in projects" :key="`project${i}`">
        <Project :project="project"/>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
  import Project from '~/components/project';

  export default {
    components: {Project},
    data() {
      return {
        projects: [
          {
            title: "Homelab",
            description: "Lorem ipsum",
            technologies: [
              "Nuxt.js", "Vuetify"
            ]
          },
          {
            title: "0x0000",
            description: "Lorem ipsum",
            technologies: [
              "Nuxt.js", "Vuetify"
            ]
          },
          {
            title: "GeoStuff",
            description: "Lorem ipsum",
            technologies: [
              "Nuxt.js", "Vuetify"
            ]
          },
          {
            title: "GeoStuff Android",
            description: "Lorem ipsum",
            technologies: [
              "Nuxt.js", "Vuetify"
            ]
          },
          {
            title: "Spotify Shower",
            description: "Lorem ipsum",
            technologies: [
              "Nuxt.js", "Vuetify"
            ]
          },
          {
            title: "Bulgarian keyboard for FirefoxOS",
            description: "A simple application, adding Phonetic and BDS Bulgarian keyboard support to devices running FirefoxOS 2.0 and up\n" +
              "\n" +
              "The application can be found on the Firefox Marketplace",
            technologies: [
              "Nuxt.js", "Vuetify"
            ]
          },
          {
            title: "GPU/CPU temperature monitor",
            description: "Lorem ipsum",
            technologies: [
              "Nuxt.js", "Vuetify"
            ]
          },
          {
            title: "CrossbarSwitchBinaryHyperCube",
            description: "A collaborative project for creating a simulation model of the communication network used by an MPP computer with a binary hypercube architecture.\n" +
              "A paper on the subject can be found on page 52 of the fourth issue of the Scientific International Conference of Computer Sciences and Engineering: http://csejournal.cs.tu-varna.bg/cse_journal_1_2016.pdf\n",
            technologies: [
              "Java", "JavaFX"
            ],
            image: 'https://github.com/chilyashev/CrossbarSwitchBinaryHyperCube/raw/master/doc/icon.png',
            links: [
              {
                link: "https://github.com/chilyashev/CrossbarSwitchBinaryHyperCube",
                title: "Source code on GitHub",
                icon: "github"
              }
            ]
          },
          {
            title: "Share link cleaner",
            description: "Lorem ipsum",
            technologies: [
              "Nuxt.js", "Vuetify"
            ]
          },
          {
            title: "miskin.in",
            description: "Lorem ipsum",
            technologies: [
              "Nuxt.js", "Vuetify"
            ]
          },
          {
            title: "chilyashev.com",
            description: "Lorem ipsum",
            technologies: [
              "Nuxt.js", "Vuetify"
            ]
          },
          {
            title: "SMS reader",
            description: "Lorem ipsum",
            technologies: [
              "Nuxt.js", "Vuetify"
            ]
          },
        ]
      }
    }
  }
</script>


<style>
</style>
