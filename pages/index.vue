<template>
  <v-layout >
    <v-flex xs12 sm8 md3>
      <Sticky v-for="(note,i) in notes" :key="i" v-bind:title="note.title" v-bind:content="note.content" v-bind:date="note.date" />
    </v-flex>
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
            title:'Task',
            content:'Thank you for developing with Vuetify and I look forward to bringing more exciting features in the future.',
            date:'Saturday, August 31, 2019'
          },
          {
            title:'Taskyy',
            content:'Thank you for developing with Vuetify',
            date:'Saturday, August 31'
          },
          {
            title:'Task',
            content:'Thank you for developing with Vuetify and I look forward to bringing more exciting features in the future.',
            date:'Saturday, August 31, 2019'
          }
        ]
    };
  }
};
</script>
