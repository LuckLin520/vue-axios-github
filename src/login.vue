<template>
  <div class="container">
    <form class="login-form" novalidate>
      <md-input-container md-has-password>
        <label>Github Personal Token(Press Enter)</label>
        <md-input type="password" v-model="token"></md-input>
      </md-input-container>
    </form>        <!--上面输入的token要提前在https://github.com/settings/tokens/new生成，直接复制过来 -->
    <md-button  @click.stop.prevent="login" class="md-raised md-primary">generate your token</md-button>
  </div>
</template>

<script type="application/ecmascript">
  import * as types from './store/types'
  export default {
    name: '',
    data () {
      return {
        msg: '',
        token: ''
      }
    },
    mounted(){
      this.$store.commit(types.TITLE, 'Login');
    },
    methods: {
      login(){
        if (this.token) {
          console.log("ww")
          this.$store.commit(types.LOGIN, this.token)
          let redirect = decodeURIComponent(this.$route.query.redirect || '/');
          this.$router.push({
            path: redirect
          })
        }
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang='scss' rel="stylesheet/scss" type="text/css">
  .login-form{
    width: 400px;
    margin: 50px auto;
  }
</style>
