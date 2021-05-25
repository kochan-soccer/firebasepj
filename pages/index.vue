<template>
  <div class="container">
    <div class="test">
    <h1>ホーム</h1>
    <NuxtLink to="/register">新規登録</NuxtLink>
    <br />
    <NuxtLink to="/login">ログイン</NuxtLink>
    <br />
    </div>
    <NuxtLink to="/logout">ログアウト</NuxtLink>
  </div>
</template>


<script>
import firebase from '~/plugins/firebase'
export default {
  data() {
    return {
      message: 'ログインができておりません',
    }
  },
  created() {
    firebase.auth().onAuthStateChanged((user) => {
      if (user) {
        this.message = 'ログイン済みです'
      }
    })
  },
}
</script>

<style scoped>
.test {
  width: 500px;
  display: flex;
  justify-content: space-between;
  margin: 0 auto;
}
</style>