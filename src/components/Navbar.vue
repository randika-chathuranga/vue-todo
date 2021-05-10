<template>
    <nav>
        <v-toolbar flat app>
            <v-app-bar-nav-icon class="grey--text" @click="drawer = !drawer"></v-app-bar-nav-icon>
            <v-toolbar-title class="text-uppercase purple--text">
                <span class="font-weight-light red--text">ToDo</span>
                <span>Randika</span>
            </v-toolbar-title>

            <v-spacer></v-spacer>

            <!--drop down-->

    <v-menu offset-y>
        <v-btn flat color="grey" slot="activator" >Menu</v-btn>
      <v-list>
        <v-list-tile v-for="link in links" :key="link.text" @click="$router.push({path: link.route})">
          <v-list-tile-title>{{link.text }}</v-list-tile-title>
        </v-list-tile>
      </v-list>
    </v-menu>

            <v-btn flat class="grey black--text">
                <span>Sign Out</span>
                <v-icon right large class="pl-2">mdi-arrow-right</v-icon>
            </v-btn>
        </v-toolbar>


        <v-navigation-drawer v-model="drawer" app class="light-blue lighten-3">
            <v-flex class="mt-3 mb-2" >
                <Popup/>
            </v-flex>
            <v-list>
                <v-list-tile class="d-block pa-2" v-for="link in links" :key="link.text" @click="$router.push({path: link.route})">
                    <v-list-tile-action>
                        <v-icon large class="white--text">{{link.icon}}</v-icon>
                    </v-list-tile-action>
                    <v-list-tile-content>
                        <v-list-tile-title>{{link.text}}</v-list-tile-title>
                    </v-list-tile-content>
                </v-list-tile>
            </v-list>
        </v-navigation-drawer>
    </nav>
</template>

<script>
import Popup from './Popup.vue'
export default {
    components :{
        Popup
    },
    data() {
        return {
            drawer: false,
            links:[
                {icon:'mdi-apps', text:'Dashbord', route:'/'},
                {icon:'mdi-folder', text:'My Projects', route:'/projects'},
                {icon:'mdi-account', text:'Team', route:'/team'}
            ],
        }
    },

}
</script>