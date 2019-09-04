<template>
  <v-hover  v-slot:default="{ hover }">
    <v-card :color="cardColor" :dark="isPinned" tile hover max-width="300" width="200">
      <v-card-title>{{title}}</v-card-title>
      <v-card-text>
        <em>
          <small>{{date}}</small>
        </em>
      </v-card-text>

      <v-card-actions>
        <div class="text-xs-right">
          <v-btn icon :hidden="!hover">
            <v-icon small @click="togglePin()">{{pinIcon}}</v-icon>
          </v-btn>
          <v-btn icon :color="transparent">
          </v-btn>
        </div>
        <div class="flex-grow-1"></div>

        <v-btn icon :disabled="isPinned" :hidden="!hover">
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
      transparent: "rgba(0, 0, 0, 0)"
    };
  },
  methods: {
    removeNote: function(id) {
      this.$emit("remove-Note", id);
    },
    togglePin : function(){
        this.setPin(!this.isPinned)
    },
    setPin : function(bool){
        this.cardColor = bool?'cyan':'white'
        this.pinIcon = bool?'mdi-pin-off':'mdi-pin'
        this.isPinned = bool
        this.updateNote({pinned:this.isPinned})
    },
    updateNote : function(note){
        this.$emit('update-Note', this.id,note)
    }
  },
  mounted(){
        this.setPin(this.pinned)
  }
};
</script>


<style>


</style>