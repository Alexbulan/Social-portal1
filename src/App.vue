<template>
   <v-app id="app">
      <v-navigation-drawer  color="green"
                            dark
                            expand-on-hover
                            hide-overlay
                            permanent
                            right
                            app>

      <v-list nav shaped dense>
        <v-list-item two-line>
          <v-list-item-avatar>
            <img src="https://secure.webtoolhub.com/static/resources/icons/set113/f9a6ef38.png">
          </v-list-item-avatar>
          <v-list-item-content class="text-left">
            <v-list-item-title class="font-weight-black">SocialLink</v-list-item-title>
            <v-list-item-subtitle>Alex Bulanov</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
        <v-divider class="my-3"></v-divider>


        <v-list-item link to="/">
          <v-list-item-icon>
            <v-icon>mdi-home-outline</v-icon>
          </v-list-item-icon>
          <v-list-item-content class="text-left">
            <v-list-item-title class="text-left">Главная</v-list-item-title>
          </v-list-item-content>
        </v-list-item>


        <v-list-item link to="/profile/1">
          <v-list-item-icon>
            <v-icon>mdi-face</v-icon>
          </v-list-item-icon>
          <v-list-item-content class="text-left">
            <v-list-item-title class="text-left">Моя страница</v-list-item-title>
          </v-list-item-content>
        </v-list-item>


        <v-list-item link to="/users">
          <v-list-item-icon>
            <v-icon>mdi-contacts</v-icon>
          </v-list-item-icon>
          <v-list-item-content class="text-left">
            <v-list-item-title class="text-left">Пользователи</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        

      </v-list>

      </v-navigation-drawer>
    
    <v-content class="px-12 py-3">
      <v-container fluid>
        <router-view v-on:login ="updateUser" :user ="user"/>
      </v-container>
    </v-content>

  </v-app>
</template>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>

<script>
export default {
  data(){
    return {
      user: {},
    }
  },

mounted:{
  updateUser(user){
  this.user = user
}
}
}

</script>