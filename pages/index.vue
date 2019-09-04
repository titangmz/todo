<template>
  <v-card class="mx-auto pa-5" max-width="1000" flat>
    <v-toolbar flat>
      <v-text-field @keyup.enter="newNote(tempNote)" v-model="tempNote" label="Task" hide-details  clearable ></v-text-field>
    

      <v-btn  @click="newNote(tempNote)" icon>
        <v-icon color="indigo lighten-1">mdi-plus-box</v-icon>
      </v-btn>
    </v-toolbar>


    <v-container fluid>
      <v-row align="center" justify="center">
        <v-card v-if="notes.length==0?true:false" max-width="500" class="pa-8" width="250" outlined>
          <v-card-text>
             Task box is empty
          </v-card-text>
        </v-card>
        <Note
          class="ma-3 pa-3 flex-grow-1"
          v-for="(note,i) in notes"
          :key="i"
          v-bind:id="note.id"
          v-bind:title="note.title"
          v-bind:content="note.content"
          v-bind:date="note.date"
          v-bind:pinned="note.pinned"
          v-on:remove-Note="removeNote"
          v-on:update-Note="setNote"
        />
      </v-row>
    </v-container>
  </v-card>
</template>


<script>
import Note from "@/components/Note";
export default {
  components: {
    Note
  },
  data() {
    return {
      tempNote:'',
      lastId:0,
      notes: [
      ]
    };
  },
  methods:{
    getDateString: function(){
        const date = new Date()
        const months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"]
        const days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"]
        const res = `${date.getDate()}/${date.getMonth()}/${date.getFullYear()}`
        return res
    },
    newNote: function(txt){
        const note = {
          pinned : false,
          title : txt,
          date : this.getDateString(),
          id : this.lastId + 1
        }
        if(txt !== ""){
          this.notes.unshift(note)
          this.lastId ++
          this.tempNote = "";
          this.updateNotes()
        }
        
    },
    removeNote : function(id){
        const tempNotes = this.notes.filter((index)=>index.id!=id)
        this.notes = tempNotes
        this.updateNotes()
    },
    updateNotes : function(){
        this.setLSNote()
        this.getLSNote()
    },
    getLSNote : function(){
      if(localStorage.notes){
        this.lastId = Number(localStorage.lastId)
        this.notes = JSON.parse(localStorage.notes)
      }
    },
    setLSNote : function(){
      localStorage.setItem('lastId' , this.lastId)
      localStorage.setItem('notes',JSON.stringify(this.notes))
    },
    setNote : function(id,note){
        const tempNote = this.notes.find((index)=>{
            return index.id === id
        })
        if(note.id !== undefined){
          tempNote.id = note.id
        }
        if(note.date !== undefined){
          tempNote.date = note.date
        }
        if(note.title !== undefined){
          tempNote.title = note.title
        }
        if(note.pinned !== undefined){
          tempNote.pinned = note.pinned
        }
        this.updateNotes()
    },

  },
  mounted(){
    this.getLSNote()
  },

};
</script>
