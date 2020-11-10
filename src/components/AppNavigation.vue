<template>
<span>
        <v-navigation-drawer app v-model="drawer" class="indigo darken-4" dark disable-resize-watcher>
            <v-list>
                <template v-for="(item, index) in items">
                    <v-list-tile :key="index">
                        <v-list-tile-content>
                            {{item.title}}
                        </v-list-tile-content>
                    </v-list-tile>
                    <v-divider :key="`divider-${index}`"></v-divider>
                </template>
            </v-list>
        </v-navigation-drawer>
<v-toolbar app color="indigo darken-4" dark>
    <v-toolbar-side-icon class="hidden-md-and-up" @click="drawer = !drawer"></v-toolbar-side-icon>
    <v-spacer class="hidden-md-and-up"></v-spacer>
    <v-toolbar-title>{{appTitle}}</v-toolbar-title>
    <v-btn text class="hidden-sm-and-down">Menu</v-btn>
    <v-spacer class="hidden-sm-and-down"></v-spacer>
    <v-btn text class="hidden-sm-and-down">SIGN IN</v-btn>
    <v-btn color="brown lighten-3" class="hidden-sm-and-down">JOIN</v-btn>
</v-toolbar>
</span>
</template>

<script>
export default {
    name: 'AppNavigation',
      data() {
        return {
            appTitle: 'Culture-Map',
            drawer: false,
            items: [
                { title: 'Menu' },
                { title: 'Sign In' },
                { title: 'Join' }
            ]
        };
    }
};
</script>

<style scoped>
</style>