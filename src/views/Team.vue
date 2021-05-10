<template>
  <div class="team">
    <h1 class="subheading grey--text">Team</h1>

    <v-container class="my-5">
        <v-layout row wrap>
          <v-flex xs12 sm6 lg3 v-for="person in team" :key="person.name">
            <v-card flat class="text-center ma-4">
              <v-responsive class="pt-4">
                <v-avatar size="100" class="grey lighten-2">
                  <v-img :src="person.avatar"></v-img>
                </v-avatar>
              </v-responsive>
              <v-card-text>
                <div class="subheading black--text">{{person.name}}</div>
                 <div class="grey--text">{{person.role}}</div>
              </v-card-text>
              <v-card-actions>
                <v-btn flat> 
                  <v-icon left small>mdi-message</v-icon>
                  <span class="text-lowercase">message</span>
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-flex>
        </v-layout>
    </v-container>
  </div>
</template>

<script>
  export default {
    data(){
      return{
        team: [
        {name:'amal', role: 'webdeveloper',avatar: '../components/1.jpg'},
        {name:'sarath', role:'graphic designer',avatar: '../components/2.jpg'},
        {name:'nimal', role:'webdeveloper',avatar: '../components/3.jpg'},
        {name:'kamal', role:'social media maveric',avatar: '../components/4.jpg'},
        {name:'dhasa', role:'cameraman',avatar: '../components/5.jpg'}
      ]
      }
    }
  }
</script>