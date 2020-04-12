<template>
  <v-app>
    <v-content class="main-container" v-if="isShowLogin "> 
        <v-row class="contain" >

          <v-col cols="6" class="form-side ">
            <div >
              <v-icon color="red" size="100px" style="margin-bottom: -15px">mdi-glasses</v-icon>
              <h1 class="titles">Login To Your  Account </h1>
              <v-text-field
                label="Username"
                dark
                color="primary"
                outlined
                v-model="usernameValue"
              ></v-text-field>
              <v-text-field
                label="Password"
                dark
                color="primary"
                outlined
                v-model="passwordValue"
              ></v-text-field>
              <v-btn block color="red" dark style="margin-bottom: 10px" @click="login">LOGIN</v-btn>
              <span style="color: white;">Or <a style="font-weight: bold" @click="changeView"> REGISTER!</a></span>
            </div>
          </v-col>

          <v-col cols="5" style="padding: 0; z-index: 10">
            <div class="img-side"></div>
          </v-col>

          <v-col cols="1" style="display: flex; justify-content: flex-end; align-items: center; flex-direction: column">
            <p class="sign" style="margin-bottom: -75px">SIGN IN</p>
          </v-col>

        </v-row>
    </v-content> 
    <v-content class="main-container" v-else>
        <v-row class="contain" style="margin: 0; position: fixed; bottom: 0">

          <v-col cols="1" style="display: flex; justify-content: flex-start; align-items: center; flex-direction: column">
            <p class="log" style="margin-top: -75px">SIGN UP</p>
          </v-col>

          <v-col cols="5" class="form-side2 ">
            <div >
              <v-icon color="red" size="100px" style="margin-bottom: -15px">mdi-boombox</v-icon>
              <h1 class="titles">Create New Account </h1>
              <v-text-field
                label="Email"
                dark
                color="primary"
                outlined
                v-model="emailValue"
              ></v-text-field>
              <v-text-field
                label="Username"
                dark
                color="primary"
                outlined
                v-model="usernameValue"
              ></v-text-field>
              <v-text-field
                label="Password"
                dark
                color="primary"
                outlined
                v-model="passwordValue"
              ></v-text-field>
              <v-btn block color="red" dark style="margin-bottom: 10px" @click="register">Register</v-btn>
              <span style="color: white;">Have An Account ? <a style="font-weight: bold" @click="changeView"> LOGIN</a></span>
            </div>
          </v-col>

          <v-col cols="6" style="padding: 0; z-index: 10">
            <div class="img-side2"></div>
          </v-col>

        </v-row>
    </v-content>
  </v-app> 
</template> 

<script>

export default {
  name: 'App',
  data: () => ({
    isShowLogin: true,
    users: [],
    emailValue: '',
    usernameValue: '',
    passwordValue: ''
  }),
  methods: {
    changeView() {
      this.isShowLogin = !this.isShowLogin,
      this.usernameValue = null
      this.passwordValue = null
      this.emailValue = null
    },
    register() {
      this.users.push(this.emailValue, this.usernameValue, this.passwordValue);
      alert(
        `   
          Your Email : ${this.emailValue} \n 
          Your Username : ${this.usernameValue} \n
          Your Password : ${this.passwordValue}
        `
      )
      this.usernameValue = ''
      this.passwordValue = ''
      this.emailValue = ''
    },
    login() {
      this.users.push(this.usernameValue, this.passwordValue);
      alert(
        `   
          Your Username : ${this.usernameValue} \n
          Your Password : ${this.passwordValue}
        `
      );
      this.usernameValue = ''
      this.passwordValue = ''
    }
  }
};
</script>

<style lang="css">
@import url('https://fonts.googleapis.com/css2?family=Anton&display=swap');

  .main-container {
    background-color: #232323
  }
  .contain {
    width: 100%; 
    height: 85%;  
    margin: 0
  }
  .img-side {
    background: url('~@/assets/login-bg.png') no-repeat top ;
    background-size: cover;
    text-align: center;
    height: 100%;
    width: 100%;
    border-right: 2px solid red;
    border-bottom: 2px solid red;
  }

  .img-side2 {
    background: url('~@/assets/register-bg.jpg') no-repeat top ;
    background-size: cover;
    text-align: center;
    height: 100%;
    width: 100%;
    border-top: 2px solid red;
  }

  .form-side {
    background-color: #393738;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    border-bottom: 2px solid red;
  }
  .form-side2 {
    background-color: #393738;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    border-top: 2px solid red;
    border-left: 2px solid red;
  }
  .sign {
    background: -webkit-linear-gradient(rgb(5, 0, 0), rgb(151, 0, 0));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    text-align: right; 
    writing-mode: vertical-rl; 
    font-size: 35px; 
    letter-spacing: 12px; 
    font-family: 'Anton', sans-serif;
  }
  .log {
    background: -webkit-linear-gradient(rgb(5, 0, 0), rgb(151, 0, 0));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    text-align: right; 
    writing-mode: vertical-lr; 
    font-size: 35px; 
    letter-spacing: 12px; 
    font-family: 'Anton', sans-serif;
  }
  .titles {
    letter-spacing: 3px; 
    color: #eaeaea; 
    margin-bottom: 45px; 
    font-size: 35px
  }
</style>