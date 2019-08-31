<template>
  <v-layout>
    <v-row>
      <v-col>
        <v-flex xs12 sm8 md3>
      <Sticky class="ma-3 pa-3" v-for="(note,i) in notes" :key="i" v-bind:title="note.title" v-bind:content="note.content" v-bind:date="note.date" />
    </v-flex>
      </v-col>
    </v-row>
  </v-layout>
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
            title:'Important',
            content:'YOOOOOOOOOOOO',
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
