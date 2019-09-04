<template>
  <v-card max-width="500" width="250">
    <v-card-title>{{title}}</v-card-title>
    <v-card-text>
      <hr class="my-3" />
    </v-card-text>
    <v-card-actions>
      <div class="text-xs-right">
        <em>
          <small>{{date}}</small>
        </em>
      </div>
      <div class="flex-grow-1"></div>
      
      <v-btn icon>
            <v-icon @click="removeSticky(id)">mdi-delete</v-icon>
          </v-btn>
    </v-card-actions>
  </v-card>
</template>


<script>
    export default{
        name:'Sticky',
        props:{
            id : Number ,
            title : String,
            date : String
        },
        methods:{
          removeSticky : function(id){
            this.$emit('remove-sticky',id)
          }
        }
    }
</script>