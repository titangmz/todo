<template>
  <v-app>
    <v-system-bar color="indigo"></v-system-bar>
    <v-navigation-drawer v-if="navigation" v-model="drawer" fixed app>
      <v-list>
        <v-list-item v-for="(item, i) in items" :key="i" :to="item.to" router exact>
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      color="indigo"
      dark
      app
    >

      <v-app-bar-nav-icon v-if="navigation" @click.stop="drawer = !drawer" />
      <v-icon class="pl-10 pr-3">mdi-file-word-box</v-icon>


      <v-toolbar-title v-text="title" />
      <v-spacer />
      <v-menu
        left
        bottom
      >
        <template v-slot:activator="{ on }">
          <v-btn icon v-on="on">
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn>
        </template>

        <v-list>
          <v-list-item
            v-for="(option,i) in options"
            :key="i"
            @click="() => {option.action()}"
          >
            <v-list-item-title>{{ option.title }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>

  </v-app>
</template>

<script>
export default {
  data() {
    return {
      navigation:false,
      drawer: false,
      fixed: false,
      options:[
        {
          icon: "mdi-apps",
          title: "Username",
          action:function(){
            alert(`${this.title}`)
          }
        },
        {
          icon: "mdi-logout",
          title: "ClearLocalStorage",
          action:function(){
            localStorage.clear()
            alert(`${this.title}`)
          }
        }
      ],
      items: [
        {
          icon: "mdi-apps",
          title: "Welcome",
          to: "/"
        },
        {
          icon: "mdi-chart-bubble",
          title: "Inspire",
          to: "/inspire"
        }
      ],
      right: true,
      rightDrawer: false,
      title: "Dodo"
    };
  }
};
</script>
