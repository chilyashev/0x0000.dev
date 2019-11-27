<!--suppress HtmlUnknownTag -->
<template>
    <v-list color="transparent">
        <v-list-item
                v-for="(project, i) in projects"
                :key="i"
        >
            <v-list-item-icon>
                <v-img
                        v-if="project.image !== undefined"
                        :src="project.image"
                        :alt="`${project.title} image`"
                        class="grey darken-4"
                        height="40"
                        width="40"
                        aspect-ratio="2.75"></v-img>
                <v-img
                        v-else
                        :alt="`${project.title} image`"
                        class="grey darken-4"
                        height="40"
                        width="40"
                        aspect-ratio="2.75"></v-img>
            </v-list-item-icon>
            <v-list-item-content>
                <v-list-item-title class="font-weight-bold">{{project.title}}</v-list-item-title>
                <v-list-item-subtitle class="mb-2 mt-1">
                    <v-chip-group
                            column
                            active-class="primary--text"
                    >
                        <v-chip v-for="(tech, index) in project.technologies" :key="`tech${index}`" x-small
                                :color="`brown darken-${1+index % 5}`" class="mr-1">
                            {{tech}}
                        </v-chip>
                    </v-chip-group>
                </v-list-item-subtitle>
                <p class="font-weight-light">{{project.description}}</p>

                <v-btn-toggle class="mt-2 mb-1">
                    <v-btn v-for="(link, linkIndex) in project.links"
                           :key="`projectLink${linkIndex}`"
                           :href="link.link"
                           small
                           text>
                        {{link.title}}
                    </v-btn>
                </v-btn-toggle>
                <v-divider></v-divider>
            </v-list-item-content>
        </v-list-item>
    </v-list>
</template>

<script>
    export default {
        name: 'ProjectList',
        data() {
            return {
                projects: [
                    {
                        expand: false,
                        title: "Homelab",
                        description: "\n" +
                            "I currently run an enterprise infrastructure at home utilizing virtualization. It mainly serves me as a NAS and also provides continuous integration for my projects.\n",
                        image: "https://img.chilyashev.com/2019/04/HwHzzGC.png",
                        technologies: [
                            'VMware ESXi',
                            'pfSense', 'HAProxy', 'OpeNVPN', 'Let\'s Encrypt',
                            'Grafana', "InfluxDB", 'Telegraf', 'SNMP',
                            'Jenkins'
                        ],
                        links: [
                            {
                                link: "https://chilyashev.com/2019/06/lab/",
                                title: "Details",
                                icon: "github"
                            },
                            {
                                link: "https://img.chilyashev.com/2019/04/HwHzzGC.png",
                                title: "Diagram"
                            },
                        ]
                    },
                    {
                        title: "chilyashev.com",
                        description: "My personal blog since around 2006. It went through being self-hosted at home, then on multiple shared hostings. Currently hosted at SiteGround.",
                        image: 'https://i.imgur.com/yXHd10S.png',
                        technologies: [
                            "WordPress"
                        ],
                        links: [
                            {
                                link: 'https://chilyashev.com',
                                title: 'Visit'
                            }
                        ]
                    },
                    {
                        title: "miskin.in",
                        description: "A doplet in DigitalOcean used as a front for various projects. This website is hosted there. There are also multiple services behind this domain (my entire home network, for example).",
                        image: 'https://miskin.in/images/bigassimg.png',
                        technologies: [
                            "Apache", "Linux administration"
                        ],
                        links: [
                            {
                                link: 'https://miskin.in',
                                title: 'Visit'
                            }
                        ]
                    },
                    {
                        title: "0x0000.dev",
                        image: 'https://i.imgur.com/y1g2eut.png',
                        description: "This personal website. Currently in its early stages",
                        technologies: [
                            'Vue.js', 'Nuxt.js', 'Vuetify'
                        ],
                        links: [
                            {
                                link: 'https://github.com/chilyashev/0x0000.dev',
                                title: 'GitHub'
                            }
                        ]
                    },
                    {
                        title: "GeoStuff",
                        description: "A desktop application used for solving basic geodetic problems.",
                        image: 'https://img.chilyashev.com/2009/12/main_screen.png',
                        technologies: [
                            "C#", ".NET",
                            'Java (for older versions)', 'Swing (for older versions)'
                        ],
                        links: [
                            {
                                link: 'https://chilyashev.com/geostuff',
                                title: 'Download'
                            }
                        ]
                    },
                    {
                        title: "GeoStuff Android",
                        description: "An Android application for solving common geodetic problems.",
                        image: 'https://img.chilyashev.com/2016/12/device-2016-12-29-000742.png',
                        technologies: [
                            "Java", "Android"
                        ],
                        links: [
                            {
                                link: 'https://play.google.com/store/apps/details?id=com.chilyashev.geostuff',
                                title: 'Download'
                            }
                        ]
                    },
                    {
                        title: "Share link cleaner",
                        description: "This app adds items to your Android share menu which remove redirects and tracking information from URLs.\n",
                        image: 'https://i.imgur.com/PBQLgzY.png',
                        technologies: [
                            "Android", "Spring Boot"
                        ],
                        links: [
                            {
                                title: 'Download',
                                link: 'https://play.google.com/store/apps/details?id=com.chilyashev.sharelinkcleaner'
                            }
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
                        title: "Spotify Shower",
                        description: "An application used for displaying the song currently playing on Spotify's desktop client.\n" +
                            "The different thing about this application is that the song name can be shown under the Windows taskbar",
                        image: 'https://img.chilyashev.com/2016/05/settings_screen.png',
                        technologies: [
                            'C', 'WIN32 API',
                            'C#', '.NET'
                        ],
                        links: [
                            {
                                title: 'Details',
                                link: 'https://chilyashev.com/2016/05/spotify-shower/'
                            }
                        ]
                    },
                    {
                        title: "Bulgarian keyboard for FirefoxOS",
                        description: "A simple application, adding Phonetic and BDS Bulgarian keyboard support to devices running FirefoxOS 2.0 and up\n" +
                            "\n" +
                            "The application can be found on the Firefox Marketplace",
                        image: 'https://img.chilyashev.com/2014/08/1489471-320x198.png',
                        technologies: [
                            "JavaScript", "HTML", "CSS"
                        ]
                    },
                    {
                        title: "GPU/CPU temperature monitor",
                        description: "An application that reads MSI Afterburner's shared memory and sends some stats to an Arduino via a serial port.",
                        image: 'https://i.imgur.com/JNvnCZn.jpg',
                        technologies: [
                            "C#", ".NET", "C", "C++", "Arduino"
                        ],
                        links: [
                            {
                                link: 'https://github.com/chilyashev/AfterburnerMonitor',
                                title: 'GitHub'
                            }
                        ]
                    },
                    {
                        title: "SMS reader",
                        description: "A simple application for getting all the SMSes stored on the Huawei mobile modems. I made it, because my provider at the time only had a Windows application, and I needed to check the messages using Linux.\n",
                        technologies: [
                            "C++"
                        ],
                        links: [
                            {
                                link: 'https://github.com/chilyashev/smsread',
                                title: 'GitHub'
                            }
                        ]
                    },
                ]
            }
        }
    }
</script>


<style>
</style>
