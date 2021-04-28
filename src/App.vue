<template>
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      app
      temporary
    >
    <div >
          <v-avatar rounded-50 size="90" class="ml-7 mt-2">
              <v-img src="https://randomuser.me/api/portraits/women/85.jpg"></v-img>
          </v-avatar>
    </div>

      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="title">
            Test User
          </v-list-item-title>
          <v-list-item-subtitle>
            Task Manager App
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list
        dense
        nav
      >

        <v-list-item
          v-for="item in items"
          :key="item.title"
          :to ="item.to"
          link
        >

          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>

    </v-navigation-drawer>

    <v-app-bar
      app
      
      color="primary"
      dark
      shrink-on-scroll
      src="projectmanage.jpg"
      prominent
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
        ></v-img>
      </template>

      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-app-bar-title>Task Manager</v-app-bar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      

    
    </v-app-bar>
    
    

    <v-main>
       <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>
  export default {
    data: () => ({ drawer: null,
    items: [
          { title: 'Task', icon: 'mdi-format-list-checks', to: '/' },
          { title: 'About', icon: 'mdi-help-box', to:'/about' },
        ],
        right: null, }),
  }
</script>