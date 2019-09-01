<template>
  <v-card max-width="500" width="250">
    <v-card-title>{{title}}</v-card-title>
    <v-card-text>
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
            date : String
        }
    }
</script>