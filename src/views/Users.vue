<template>
  <div class="home">
<!--    <img alt="Vue logo" src="../assets/logo.png"> -->
 <!--   <HelloWorld msg="Welcome to Your Vue.js App"/> -->

  <v-row>
    <v-col cols="6">
    <UserIcon 
        :name="users[0].name"
        :username="users[0].username"
        id=1
    ></UserIcon>
    </v-col>
    <v-col cols="6">
    <UserIcon 
        :name="users[1].name"
        :username="users[1].username"
        id='2'
    ></UserIcon>
    </v-col>
  </v-row>

  <v-row>
    <v-col cols="6">
    <UserIcon 
        :name="users[2].name"
        :username="users[2].username"
        id=3
    ></UserIcon>
    </v-col>
    <v-col cols="6">
    <UserIcon 
        :name="users[3].name"
        :username="users[3].username"
        id='4'
    ></UserIcon>
    </v-col>
  </v-row>

  <v-row>
    <v-col cols="6">
    <UserIcon 
        :name="users[4].name"
        :username="users[4].username"
        id=5
    ></UserIcon>
    </v-col>
    <v-col cols="6">
    <UserIcon 
        :name="users[5].name"
        :username="users[5].username"
        id='6'
    ></UserIcon>
    </v-col>
  </v-row>

  <v-row>
    <v-col cols="6">
    <UserIcon 
        :name="users[6].name"
        :username="users[6].username"
        id='7'
    ></UserIcon>
    </v-col>
    <v-col cols="6">
    <UserIcon 
        :name="users[7].name"
        :username="users[7].username"
        id='8'
    ></UserIcon>
    </v-col>
  </v-row>

  <v-row>
    <v-col cols="6">
    <UserIcon 
        :name="users[8].name"
        :username="users[8].username"
        id='9'
    ></UserIcon>
    </v-col>
    <v-col cols="6">
    <UserIcon 
        :name="users[9].name"
        :username="users[9].username"
        id='10'
    ></UserIcon>
    </v-col>
  </v-row>
  
  </div>
</template>

<script>
import UserIcon from '@/components/UserIcon.vue'
export default {
  components: {
    UserIcon
  },
  data(){
    return{
      users: [],
    }
  },
  methods:{
    loadUsers(){
      let url = 'http://jsonplaceholder.typicode.com/users'
        this.$axios.get(url).then(response=>{
          this.users = response.data
      })
    }
  },
  mounted(){
        this.loadUsers()
  },
  watch:{
    $route(){
        this.loadUsers()
    }
  }
}
</script>

<template>
    <div :v-if="profile!== null">
        <v-row class="text-left">
            <v-col cols="10">
                <h1 class="green--text text--darken-2">
                    <v-icon large color="green darken-2">mdi-account-outline</v-icon>
                    {{profile.name}}
                </h1>
            </v-col>
        </v-row>
        <v-row class="text-left">
            <v-col cols="2">
                <img :src="avatar" style="max-width: 100%">
            </v-col>
            <v-col cols="10" class="text-left">
                <p>
                    Веб-сайт: <a :href="profile.website" target="_blank">{{profile.website}}</a>
                </p>
                <p>
                    E-mail: <a href="mailto:...">{{profile.email}}</a>
                </p>
                <p>
                    Город: {{profile.address.city}}
                </p>
                <p>
                    Место работы: {{profile.company.name}}
                </p>
            </v-col>
        </v-row>

        <v-col cols="10">
        <Post v-for="(post, index) in posts" 
        :key="index"
        
        :title="post.title"
        :body="post.body"
        :author="profile.name"
        :avatar="avatar"
        ></Post>
        </v-col>
    </div>
</template>
