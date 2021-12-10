<template>
  <div>
      <h2>로그인 유지<input type="checkbox" v-model="setlogin" ></h2>
        <input type="text" placeholder="아이디" v-model="username"><br>
        <input type="password" placeholder="비밀번호" v-model="userpassword" @keyup.enter="login()"><br>
        <button v-on:click="login" type="submit" >LOGIN</button><br>
    <!-- <h3><router-link to="/findid">아이디 찾기</router-link>&nbsp;&nbsp;&nbsp; | <router-link to="/findpw">&nbsp;&nbsp;&nbsp;비밀번호 찾기</router-link></h3> -->
    <button class="bt_signup_form" v-on:click="signup">회원가입</button>
  </div>
</template>

<script>
export default {
    data() {
        return{
            username: '',
            userpassword: '',
            setlogin: false
        }
    },
    methods: {
        login() {
            this.$store.dispatch('login',  {username: this.username, password: this.userpassword, setlogin: this.setlogin})
        },
        signup() {

        },
        // staylogin() {
        //     this.off =! this.off

        //     if(this.off == true) {
        //         if(this.username == ""){
        //             this.username = JSON.parse(localStorage.getItem("user")).sigid
        //         }if(this.userpassword == "") {
        //             this.userpassword = JSON.parse(localStorage.getItem("user")).sigpw
        //         }
        //         else{
        //             this.username = JSON.parse(localStorage.getItem("user")).sigid
        //             this.userpassword = JSON.parse(localStorage.getItem("user")).sigpw
        //         }
        //     }
        //     // console.log(this.off);
        //     // this.username = localStorage.getItem("user").sigid
        //     // console.log(this.username);
        //     // this.userpassword = localStorage.getItem("user").sigpw
        // }
    }

}
</script>

<style>

</style>