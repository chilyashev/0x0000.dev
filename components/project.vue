<!--suppress XmlUnboundNsPrefix, HtmlUnknownBooleanAttribute, HtmlUnknownTag -->
<template>
    <v-card>
        <v-img v-if="project.image"
               :src="project.image"
               aspect-ratio="2.75"
        ></v-img>
        <v-card-title primary-title>
            <div>
                <h3 class="headline mb-0">{{ project.title }}</h3>
                <div> {{ project.description }}</div>
                <div>
                    <v-chip v-for="(tech, index) in project.technologies" :key="`tech${index}`">{{tech}}</v-chip>
                </div>
            </div>
        </v-card-title>

        <v-divider v-if="project.links !== undefined && project.links.length > 0"></v-divider>

        <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn v-for="(link, linkIndex) in project.links" :key="`projectLink${linkIndex}`" :href="link.link" flat>
                {{link.title}}
            </v-btn>
            <!--<v-btn flat color="orange"
                   @click="toggleDetails()">
                <v-icon>chevron_right</v-icon>
            </v-btn>-->
        </v-card-actions>


        <v-slide-y-transition>
            <v-card-text v-show="expanded">
                <div class="text-lg-right"><b>DOB: </b>whatever</div>
            </v-card-text>
        </v-slide-y-transition>
    </v-card>
</template>

<script>
    export default {
        name: "Project",
        props: {
            project: {
                type: Object
            }
        },
        data() {
            return {
                expanded: false
            }
        },
        methods: {
            toggleDetails() {
                this.expanded = !this.expanded
            }
        }
    }
</script>

<style scoped>

</style>
