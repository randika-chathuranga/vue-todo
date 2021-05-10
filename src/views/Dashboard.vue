<template>
  <div class="dashboard">
    <h1 class="subheading grey--text">Dashboard</h1>

    
  <v-container class="my-5">

    <v-layout row class="mb-3 pa-3">
    <v-tooltip bottom>
      <template v-slot:activator="{ on, attrs }">
      <v-btn flat @click="sortBy('title')" v-bind="attrs" v-on="on" >
        <v-icon left small>mdi-folder</v-icon>
        <span class="text-lowercase">by project name</span>
      </v-btn>
      </template>
      <span>sort by project name</span>
    </v-tooltip>


      <v-tooltip bottom>
      <template v-slot:activator="{ on, attrs }" >
      <v-btn flat class="ml-2" @click="sortBy('person')" v-bind="attrs" v-on="on" >
        <v-icon left small>mdi-account</v-icon>
        <span class="text-lowercase">Person</span>
      </v-btn>
      </template>
      <span>sort by person</span>
    </v-tooltip>

      

    </v-layout>
    <v-card flat class="pa-3" v-for="project in projects" :key="project.title">
      <v-layout row wrap :class="`pa-3 project ${project.status}}`">
        <v-flex xs12 md6>
          <div class="caption grey--text">Project Title</div>
          <div>{{project.title}}</div>
        </v-flex>

        <v-flex xs6 sm4 md2>
          <div class="caption grey--text">Person</div>
          <div>{{project.person}}</div>
        </v-flex>

        <v-flex xs6 sm4 md2>
          <div class="caption grey--text">Due by</div>
          <div>{{project.due}}</div>
        </v-flex>

        <v-flex xs2 sm4 md2>
          <div>
            <v-chip small :class="`${project.status} black--text caption my-2`">{{project.status}}</v-chip>
          </div>
        </v-flex>
        <v-divider></v-divider>
      </v-layout>
    </v-card>
  </v-container>
  </div>
</template>

<script>
  export default{
    data(){
      return{
        projects: [
        {title:"a",person:"b",due:"c",status:"ongoing",content:"lorem"},
        {title:"z",person:"e",due:"f",status:"complete",content:"lorem"},
        {title:"g",person:"h",due:"i",status:"complete",content:"lorem"},
        {title:"j",person:"k",due:"l",status:"overdue",content:"lorem"},
      ],
      
    }
  },
  methods:{
    sortBy(prop){
      this.projects.sort((a,b)=> a[prop] < b[prop] ? -1 : 1)
    }
  }
  }
</script>


<style>
  .project.complete{
    border-left: 4px solid blue
  }

  .project.ongoing{
    border-left: 4px solid orange
  }

  .project.overdue{
    border-left: 4px solid green
  }

  .v-chip.complete{
  background: red
  }

  .v-chip.ongoing{
  background: solid green
  }

  .v-chip.overdue{
  background: solid yellow 
  }
</style>