<template>
  <form v-on:submit.prevent="submitForm">
    <div>
      <label for="username">id: </label>
      <input id="username" type="text" v-model="username">
    </div>
    <div>
      <label for="password">pw: </label>
      <input id="password" type="password" v-model="password">
    </div>
    <button type="submit">login</button>
  </form>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      username: '',
      password: ''
    }
  },
  methods: {
    submitForm: function() {
      // event.preventDefault() // 버튼 눌렀을 때 새로고침을 막아줌 == submit.prevent
      console.log(this.username, this.password)
      var url = 'https://jsonplaceholder.typicode.com/users';
      var data = {
        username: this.username,
        poassword: this.password
      }
      axios.post(url, data)
        .then(function(response) {
          console.log(response)
        })
        .catch(function(error) {
          console.log(error)
        })
    }
  }
}
</script>

<style>

</style>