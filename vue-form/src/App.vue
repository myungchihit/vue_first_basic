<template>
  <div>
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
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data: function() {
    return {
      username: '',
      password: '',
    }
  },
  methods: {
    submitForm: function() {  // 이벤트 버블링으로 버튼이 아닌 상위 form에서 이벤트 발생
        //event.preventDefault();  // 위에서 v-on:submit.prevent가 preventDefault와 동일함
        console.log(this.username, this.password);
        var url = 'https://jsonplaceholder.typicode.com/users';
        var data = {
          username: this.username,
          password: this.password
        }
        axios.post(url, data)
        .then(function(response) {
          console.log(response);
        })
        .catch(function(error){
          console.log(error);
        });
    }
  }
}
</script>

<style>

</style>