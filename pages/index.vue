<template>
  <v-card class="mx-auto pa-5" max-width="1000" flat>
    <v-toolbar flat>
      <v-text-field @keyup.enter="newNote(tempNote)" v-model="tempNote" label="Task" hide-details  clearable ></v-text-field>
    

      <v-btn  @click="newNote(tempNote)" icon>
        <v-icon>mdi-plus</v-icon>
      </v-btn>
    </v-toolbar>


    <v-container fluid>
      <v-row align="center" justify="center">
        <Sticky
          class="ma-3 pa-3 flex-grow-1"
          v-for="(note,i) in notes"
          :key="i"
          v-bind:title="note.title"
          v-bind:content="note.content"
          v-bind:date="note.date"
        />
      </v-row>
    </v-container>
  </v-card>
</template>


<script>
import Sticky from "@/components/Sticky";
export default {
  components: {
    Sticky
  },
  data() {
    return {
      tempNote:'',
      notes: [
        {
          title: "Test note",
          date: "Saturday, August 31, 2019"
        },
        {
          title: "New tast is coming",
          date: "Saturday, August 31, 2019"
        },
        {
          title: "YOLOYOLOYOLOYOLOYOLOYOLOYOLOYOLOYOLOYOLOYOLOYOLOYOLOYOLOYOLOYOLOYOLOYOLOYOLOYOLOYOLO",
          date: "Saturday, August 2, 2019"
        },
        {
          title: "from",
          date: "Saturday, August 2, 2019"
        }
        
      ]
    };
  },
  methods:{
    getDateString: function(){
        const date = new Date()
        const months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"]
        const days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"]
        const res = `${days[date.getDay()]}, ${months[date.getMonth()]} ${date.getDate()}, ${date.getFullYear()}`
        return res
    },
    newNote: function(txt){
        const note = {
          title : txt,
          date : this.getDateString()
        }
        this.notes.unshift(note)
    },
  }


};
</script>
