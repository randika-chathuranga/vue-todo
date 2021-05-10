<template>
  <div class="text-center">
    <v-dialog v-model="dialog" width="500">

      <template v-slot:activator="{ on, attrs }">
        <v-btn  color="red lighten-2" v-bind="attrs" v-on="on">Add Project</v-btn>
       </template>  
          
        <v-card>
        <v-card-title>Add new project</v-card-title>
        <v-card-text>
            <v-form class="px-3" ref="form">
                <v-text-field label="Title" v-model="title" prepend-icon="mdi-folder" :rules="inputRules"></v-text-field>
                <v-textarea label="Informations" v-model="content" prepend-icon="mdi-pen" :rules="inputRules"></v-textarea>


                <v-dialog ref="dialog" v-model="modal" :return-value.sync="date"  persistent width="290px">
                <template v-slot:activator="{ on, attrs }">
                <v-text-field  v-model="date" label="Due date" prepend-icon="mdi-calendar" readonly v-bind="attrs" v-on="on"></v-text-field>
                </template>
                <v-date-picker v-model="date" scrollable>
                <v-spacer></v-spacer>
                <v-btn text color="primary" @click="modal = false">Cancel</v-btn>
                <v-btn text color="primary"  @click="$refs.dialog.save(date)"> OK</v-btn>
                </v-date-picker>
                </v-dialog>
                <v-btn flat class="success mx-0 mt-3" @click="submit()">Add Project</v-btn>
            </v-form>
        </v-card-text>
        </v-card>
    </v-dialog>
  </div>
</template>  

<script>
export default {
    data(){
        return{
            title:"",
            content:"",
            inputRules:[
                v => v.length >= 3 || 'minimum length is 3 charecters'
            ]
        }
    },

    methods: {
        submit(){
            if(this.$refs.form.validate){
                console.log(this.title, this.content)
            }
            
        }
    },
}
</script>

          
        
          
        
      

     


     
