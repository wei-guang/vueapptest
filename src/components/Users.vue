<template>
  <div class="users">
    <h1>Users</h1>

    <form v-on:submit="addUser">
      <input type="text" v-model="newUser.name" placeholder="Enter name">
      <input type="text" v-model="newUser.email" placeholder="Enter email">
      <input type="submit" value="Submit">
    </form>

    <ul>
      <li v-for="user in users">{{user.name}}:{{user.email}}</li>
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
          },
          {
            name:"Henry Zhang",
            email:"xxxx@mail.com",
            contacted:false
          },
          {
            name:"Emily Zhang",
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
      }
    }
  }
</script>

<style scoped>

</style>
