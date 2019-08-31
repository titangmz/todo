<template>
  <v-card min-width="250">
    <v-card-title>{{title}}</v-card-title>
    <v-card-text>
      <p>{{content}}</p>

      
      <hr class="my-3" />
      <div class="text-xs-right">
        <em>
          <small>{{date}}</small>
        </em>
      </div>
    </v-card-text>
  </v-card>
</template>


<script>
    export default{
        name:'Sticky',
        props:{
            title : String,
            content : String,
            date : String
        }
    }
</script>