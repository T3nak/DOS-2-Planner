<template>
    <v-app>
        <v-tabs v-model="active" centered>
            <v-toolbar class="primary elevation-4 mb-3" dark>
                <v-toolbar-title>
                    <input v-model="name" class="inline-input" style="width: 360px;">
                </v-toolbar-title>
                <v-spacer></v-spacer>
                <v-btn icon @click="decLevel()">
                    <v-icon>remove</v-icon>
                </v-btn>
                <input v-model.number.lazy="level" @change="changeLevel()" class="text-xs-center inline-input">
                <v-btn icon @click="incLevel()">
                    <v-icon>add</v-icon>
                </v-btn>
                <v-tabs-bar slot="extension" class="primary" dark>
                    <v-tabs-item href="#attributes" ripple>Attributes</v-tabs-item>
                    <v-tabs-item href="#combat" ripple>Combat</v-tabs-item>
                    <v-tabs-item href="#civil" ripple>Civil</v-tabs-item>
                    <v-tabs-item href="#talents" ripple>Talents</v-tabs-item>
                    <v-tabs-slider></v-tabs-slider>
                </v-tabs-bar>
            </v-toolbar>
            <v-tabs-items>
                <Attributes :level="level" />
                <Combat :level="level" />
                <Civil :level="level" />
                <Talents :level="level" />
            </v-tabs-items>
        </v-tabs>
    </v-app>
</template>

<script>
    import Attributes from "~/components/Attributes.vue";
    import Combat from "~/components/Combat.vue"
    import Civil from "~/components/Civil.vue"
    import Talents from "~/components/Talents.vue";

    export default {
        components: {
            Attributes,
            Combat,
            Civil,
            Talents
        },
        data() {
            return {
                active: null,
                level: 1,
                name: "Character Name",
                attr: {
                    value: 1,
                    bonus: 0
                }
            };
        },
        methods: {
            incLevel() {
                this.level++;
            },
            decLevel() {
                if (this.level > 1) {
                    this.level--;
                }
            },
            changeLevel() {
                if (this.level < 1) {
                    debugger;
                    this.level = 1;
                }
            }
        }
    };
</script>