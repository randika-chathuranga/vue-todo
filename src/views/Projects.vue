<template>
  <div class="projects">
    <h1 class="subheading grey--text">Projects</h1>
 
  <v-container class="my-5">

   <v-expansion-panels accordion>
      <v-expansion-panel v-for="project in myprojects" :key="project.title">
        <v-expansion-panel-header>{{project.title}}</v-expansion-panel-header>
        <v-expansion-panel-content>
          <v-card>
          <v-card-text>
            <div class="font-weight-bold">{{project.due}}</div>
            <div>{{project.content}}</div>
          </v-card-text>
         </v-card>
        </v-expansion-panel-content>
      </v-expansion-panel>
    </v-expansion-panels>
  <!--
  <v-expansion-panels>
    <v-expansion-panel>
      <v-expansion-panel-content>
         <v-expansion-panel-header>Project Title</v-expansion-panel-header>
         <v-card>
          <v-card-text>
            <div class="font-weight-bold">due by xx.xx.xx</div>
            <div>Info</div>
          </v-card-text>
         </v-card>
      </v-expansion-panel-content>
    </v-expansion-panel>
  </v-expansion-panels>

  -->
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

  computed: {
    myprojects(){
      return this.projects.filter(project => {
        return project.person === 'b'
      })
    }
  }
}
</script>