<!--suppress HtmlUnknownTag, HtmlUnknownBooleanAttribute -->
<template xmlns:v-slot="http://www.w3.org/1999/XSL/Transform">
    <v-container fluid>
        <v-row>
            <v-col offset-md="3" md="6" cols="12" align="center">
                <!--<img src="~/static/images/logo.png" alt="Logo" height="60">-->
                <h1 class="display-2 font-weight-thin">Mihail Chilyashev</h1>

            </v-col>
        </v-row>
        <v-row class="mb-6">
            <v-col offset-md="3" md="6" cols="12">
                <v-list color="transparent">
                    <v-list-item-group>
                        <v-list-item
                                v-for="(link, i) in links"
                                :key="i"
                                :href="link.link"

                        >
                            <v-list-item-icon>
                                <v-icon size="56" v-text="`mdi-${link.icon}`" :color="link.color"></v-icon>
                            </v-list-item-icon>
                            <v-list-item-content>
                                <v-list-item-title class="font-weight-light">{{link.title}}</v-list-item-title>
                                <v-list-item-subtitle class="font-weight-light">{{link.subtitle}}</v-list-item-subtitle>
                                <span class="my-1 font-condensed font-weight-light">{{link.description}}</span>
                                <v-divider></v-divider>
                            </v-list-item-content>

                        </v-list-item>
                    </v-list-item-group>
                </v-list>
            </v-col>
        </v-row>

        <v-row>
            <v-col offset-md="3" md="6" cols="12" align="center">
                <h1 class=".display-2 font-weight-thin">Projects</h1>
            </v-col>
        </v-row>
        <v-row>
            <v-col offset-md="3" md="6" cols="12">
                <ProjectList></ProjectList>
            </v-col>
        </v-row>

        <v-row>
            <v-col offset-md="3" md="6" cols="12" align="center">
                <h1 class=".display-2 font-weight-thin">Experience</h1>
            </v-col>
        </v-row>
        <v-row>
            <v-col offset-md="3" md="6" cols="12">
                <v-timeline>
                    <v-timeline-item
                            v-for="(job, i) in jobs"
                            :key="i"
                            :color="job.color"
                            small
                    >
                        <template v-slot:opposite>
                                <span :class="`headline font-weight-light ${job.color}--text`"
                                      v-text="job.period"></span>
                        </template>
                        <div class="py-4">
                            <h2 :class="`headline font-weight-bold ${job.color}--text`">{{job.place}}
                            </h2>
                            <v-row>
                                <v-col>
                                </v-col>
                            </v-row>
                            <v-row>
                                <v-col>
                                    <v-chip small :color="`${job.color}`">{{job.title}}</v-chip>
                                    <v-chip-group
                                            column
                                            active-class="primary--text"
                                    >
                                        <v-chip
                                                v-for="(tech, index) in job.tech" :key="`tech${index}`"
                                                class="my-2 mx-1"
                                                small
                                                :color="`${job.color} darken-${1+index % 5}`"
                                        >
                                            {{tech}}
                                        </v-chip>
                                    </v-chip-group>
                                </v-col>
                            </v-row>
                        </div>
                    </v-timeline-item>
                </v-timeline>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
    import backgroundUrl from '~/assets/bg.jpg'
    import ProjectList from '~/components/ProjectList.vue'

    export default {
        layout: 'simple',
        head: {
            title: 'Mihail Chilyashev'
        },
        components: {ProjectList},
        computed: {
            breakpoint() {
                return this.$vuetify.breakpoint.name
            }
        },
        data() {
            return {
                bgUrl: backgroundUrl,
                links: [
                    {
                        title: 'GitHub',
                        subtitle: '@chilyashev',
                        description: 'Open source contributions and private projects',
                        icon: 'github-face',
                        link: 'https://github.com/chilyashev',
                        color: '#4078c0'
                    },
                    {
                        title: 'Blog.',
                        subtitle: 'chilyashev.com',
                        description: 'Some articles of questionable quality in Bulgarian',
                        icon: 'wordpress',
                        link: 'https://chilyashev.com',
                    },
                    {
                        title: 'LinkedIn',
                        subtitle: '',
                        description: 'Hit me up with your best offer',
                        icon: 'linkedin',
                        link: 'https://linkedin.com/in/mihail-chilyashev-b4814438',
                        color: '#2867B2'
                    },
                    {
                        title: 'Email',
                        subtitle: 'm@chilyashev.com',
                        description: this.getMailDescription(),
                        icon: 'email',
                        link: 'mailto:m@chilyashev.com',
                        //color: '#B23121'
                    },
                ],
                jobs: [
                    {
                        color: 'cyan',
                        period: 'Sep 2018 - Nov 2019',
                        title: 'Software Developer',
                        place: 'Parking Telecom Labs',
                        tech: [
                            'Java 8', 'Spring Boot', 'Android', 'Angular',
                            'Couchbase'
                        ]
                    },
                    {
                        color: 'blue',
                        period: 'Apr 2018 - Sep 2018',
                        title: 'Software Developer',
                        place: 'myPOS',
                        tech: [
                            'C++', 'Java 8', 'Android',
                            'MS SQL Server'
                        ]
                    },
                    {
                        color: 'purple',
                        period: 'Sep 2015 - Mar 2018',
                        title: 'Software Developer',
                        place: 'InterCard Finance',
                        tech: [
                            'C', 'C++', 'C#', 'Android',
                            'MS SQL Server'
                        ]
                    },
                    {
                        color: 'pink',
                        period: 'Jul 2012 - Sep 2015',
                        title: 'Web Developer',
                        place: 'InterCard Finance',
                        tech: [
                            'PHP', 'JavaScript',
                            'MySQL'
                        ]
                    },
                    {
                        color: 'green',
                        period: 'Aug 2011 - Jul 2012',
                        title: 'Web developer',
                        place: 'Freelance',
                        tech: [
                            'PHP', 'JavaScript',
                            'MySQL', 'WordPress', 'PrestaShop'
                        ]
                    }
                ]
            }
        },
        methods: {
            getMailDescription() {
                let mailDescriptions = [
                    'Doth not spam!',
                    'Spameth me not!',
                    'You shall not spam!',
                    'Ye shall not spam!',
                ];
                return mailDescriptions[Math.floor(Math.random() * mailDescriptions.length)]
            }
        }
    }
</script>


<style>
    .pulse {
        border-radius: 60%;
        cursor: pointer;
        box-shadow: 0 0 0 rgba(48, 48, 48, 0.4);
        animation: pulse 2s infinite;
        animation-iteration-count: 3;
    }

    .pulse:hover {
        animation: none;
    }

    @-webkit-keyframes pulse {
        0% {
            -webkit-box-shadow: 0 0 0 0 rgba(48, 48, 48, 0.4);
        }
        70% {
            -webkit-box-shadow: 0 0 0 4px rgba(48, 48, 48, 0);
        }
        100% {
            -webkit-box-shadow: 0 0 0 0 rgba(48, 48, 48, 0);
        }
    }

    @keyframes pulse {
        0% {
            -moz-box-shadow: 0 0 0 0 rgba(48, 48, 48, 0.4);
            box-shadow: 0 0 0 0 rgba(48, 48, 48, 0.4);
        }
        70% {
            -moz-box-shadow: 0 0 0 4px rgba(48, 48, 48, 0);
            box-shadow: 0 0 0 4px rgba(48, 48, 48, 0);
        }
        100% {
            -moz-box-shadow: 0 0 0 0 rgba(48, 48, 48, 0);
            box-shadow: 0 0 0 0 rgba(48, 48, 48, 0);
        }
    }

    .intro {
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.25);
    }
</style>
