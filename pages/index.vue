<!--suppress HtmlUnknownTag -->
<template>
    <v-content>
        <v-container>
            <h1></h1>
        </v-container>
        <v-container>
            <p>Hi there,</p>
            <p>My name is Mihail Chilyashev and I spend most of my days writing software and solving the problems this
                creates.
                <br>
                Currently, I work as a Java developer creating highly scalable microservices and cloud-native
                applications.</p>

            <p>You can find some of my projects
                <nuxt-link to="projects" flat class="pulse">here</nuxt-link>
                . Or maybe check out a more detailed CV on <a href="https://chilyashev.com/cv">my other website</a>.
            </p>
        </v-container>
    </v-content>
</template>

<script>

    export default {
        layout: 'game',
        data() {
            return {}
        },
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
</style>
