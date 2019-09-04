<template>
  <v-hover v-slot:default="{ hover }">
    <v-card :color="cardColor" :dark="isPinned" tile hover max-width="300" width="250">
      <v-card-title>{{title}}</v-card-title>
      <v-card-text>
      </v-card-text>
      <v-card-actions>
        <div class="text-xs-right">
          <v-btn icon v-bind:class="{transparent:!hover}">
            <v-icon small @click="togglePin()">{{pinIcon}}</v-icon>
          </v-btn>
          <em style="opacity:0.5">
              <small>
                {{notePinStatus?'pinned':''}}
              </small>
            </em>
          <v-btn icon :color="transparent">
          </v-btn>
        </div>
        <div class="flex-grow-1"></div>

        <v-btn icon :disabled="isPinned" v-bind:class="{transparent:!hover}">
          <v-icon small @click="removeNote(id)">mdi-delete</v-icon>
        </v-btn>
      </v-card-actions>
     
    </v-card>
  </v-hover>
</template>


<script>
export default {
  name: "Note",
  props: {
    pinned : Boolean,
    id: Number,
    title: String,
    date: String
  },
  data() {
    return {
      pinIcon : 'mdi-pin',
      isPinned : false,
      cardColor : 'white',
      transparent: "rgba(0, 0, 0, 0)",
    };
  },
  methods: {
    removeNote: function(id) {
      this.$emit("remove-Note", id);
    },
    togglePin : function(){
        this.setPin(!this.isPinned)
        this.updateNote({pinned:this.isPinned})
    },
    setPin : function(bool){
        this.cardColor = bool?'indigo lighten-1':'white'
        this.pinIcon = bool?'mdi-pin-off':'mdi-pin'
        this.isPinned = bool
    },
    updateNote : function(note){
        this.$emit('update-Note', this.id,note)
    }
  },
  computed:{
      notePinStatus : function(){
          this.setPin(this.pinned)
          return this.isPinned
      }
  },
  mounted(){
       this.setPin(this.pinned)
  }
};
</script>

<style scoped>
  .transparent{
    opacity: 0 !important;
  }
</style>