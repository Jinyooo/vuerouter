<template>
  <div id="app">
    <v-app>

      <!-- 버튼을 눌렀을 때 아래 router-view 에 로그인 화면이 뜨도록 -->
      <v-app-bar app color="primary" dark>
        <v-toolbar-title @click="$router.push('/')">blog</v-toolbar-title>
        <v-spacer></v-spacer>

        <div v-if="login">
          <v-btn outlined @click="$router.push('/board')">글목록</v-btn> 
          <v-btn outlined @click="$router.push(`/user/${user}`)">{{user}}님의 정보</v-btn>
          <v-btn @click="logout">로그아웃</v-btn>
        </div>
        
        <v-btn 
        class="black" dark 
        v-else
        @click="$router.push('/login')"
        >로그인</v-btn>
      </v-app-bar>
      <v-main>
        
        <!-- 라우터된 화면이 보이는 공간 -->
        <router-view @login-user="showLogin" />

      </v-main>

      
    </v-app>
  </div>
</template>

<script>
export default {
  name : 'App',
  data : ()=>( {
    login : false,
    user : '',
  }),
  methods : {
    showLogin : function(user) {
      this.user = user;
      this.login = true;
    },
    logout : function() {
      this.user = '';
      this.login = false;
      this.$router.push('/');
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
