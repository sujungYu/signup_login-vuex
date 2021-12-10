<template>
  <div>
      <i class="fas fa-times" v-on:click="cancel"></i>
      <form v-on:submit.prevent="check">
           <input type="text" placeholder="이름" v-model="username"><br>
           <input type="text" placeholder="이메일" v-model="usermail"><br>
           <input type="text" placeholder="아이디" v-model="userid">
           <button v-on:click.prevent="idcheck">중복확인</button><br>
           <input type="password" placeholder="비밀번호" v-model="userpassword"><br>
           <input type="password" placeholder="비밀번호 확인" v-model="checkpassword"><br>
           <button type="submit">회원가입</button>
      </form>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return{
            username: '',
            usermail: '',
            userid: '',
            userpassword: '',
            checkpassword: ''

        }
    },
    methods: {
        check() {
            if(this.userpassword != this.checkpassword) {
                alert(' 비밀번호를 다시 확인해주세요')
            }
            else {
                this.signup()
            }
        },
        signup() {
            this.$store.dispatch('signup', {username: this.username, usermail: this.usermail, userid: this.userid, userpassword: this.userpassword, checkpassword: this.checkpassword})
            this.$router.push('./login')
        },
        idcheck() {
            return new Promise((resolve, reject) => {
                axios.get(`${'http://localhost:8000'}/signup?userid=${this.userid}`).then((res) => {
                    console.log(res.data);
                if(res.data == 0 ) {
                    alert('사용가능한 아이디입니다')
                }
                else {
                    alert('이미 사용중인 아이디입니다')
                }
                resolve(res);
            }).catch((error) => {
                reject(error);
            })
            })
        },
        cancel() {
            this.$router.push('./login')
        }
    }

}
</script>

<style>

</style>