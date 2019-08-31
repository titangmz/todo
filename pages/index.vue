<template>
  <v-container fluid>
      <v-row align="center" justify="center">
       
          <Sticky  class="ma-3 pa-3 flex-grow-1" v-for="(note,i) in notes" :key="i" v-bind:title="note.title" v-bind:content="note.content" v-bind:date="note.date" />
      
      </v-row>
  </v-container>
</template>


<script>
import Sticky from "@/components/Sticky";
export default {
  components: {
    Sticky
  },
  data() {
    return {
        notes:[
          {
            title:'Task1',
            content:'Task 1 content',
            date:'Saturday, August 31, 2019'
          },
          {
            title:'Task1',
            content:'Task 1 content',
            date:'Saturday, August 31, 2019'
          },
          {
            title:'Important',
            content:'YOOOOOOOOOOOOYOOOOOOOOOOOOYOOOOOOOOOOOOYOOOOOOOOOOOOYOOOOOOOOOOOO',
            date:'Tuesday, June 22'
          },
          {
            title:'Task',
            content:'Yay',
            date:'Saturday, August 2, 2019'
          }
        ]
    };
  }
};
</script>
