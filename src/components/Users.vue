<template>
  <div class="users">
    <h1>Users</h1>

    <form v-on:submit="addUser">
      <input type="text" v-model="newUser.name" placeholder="Enter name">
      <input type="text" v-model="newUser.email" placeholder="Enter email">
      <input type="submit" value="Submit">
    </form>

    <ul>
      <li v-for="user in users">
        <input type="checkbox" class="toggle" v-model="user.contacted">
        <span :class="{contacted:user.contacted}">
          {{user.name}}:{{user.email}}
          <button v-on:click="deleteUser(user)">del</button>
        </span>
      </li>
    </ul>

  </div>
</template>

<script>
  export default {
    name: "users",
    data:function () {
      return{
        newUser:{},
        users:[
          {
            name:"Hemiaf Zhang",
            email:"xxxx@mail.com",
            contacted:false
          }
        ]
      }
    },
    methods:{
      addUser:function (e) {
        //console.log("add...");
        this.users.push({
          name:this.newUser.name,
          email:this.newUser.email,
          contacted:false
        });
        e.preventDefault();
      },

      deleteUser:function (user) {
        //console.log("jjj")
        this.users.splice(this.users.indexOf(user),1);
      }
    },
    created:function () {//重要的事情说一万遍，不要把它写到methods里！！！！！
      //console.log("jdjdjdjdj");
      this.$http.get("http://jsonplaceholder.typicode.com/users").then(function (response) {
        // console.log(response.data);
        this.users=response.data;
      })
    }
  }
</script>

<style scoped>
  .contacted{
    text-decoration: line-through;
  }
</style>
