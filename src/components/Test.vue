<template>
    <div class="test">
      <h1>{{title}}</h1>
      <p>{{user.firstname}}</p>
      <p v-text="user.lastname"></p>

      <!--v-if-->
      <p v-if="showName">{{user.firstname}}</p>
      <p v-else>Nobody</p>

      <!--v-for-->
      <ul>
        <li v-for="item in items">{{item.title}}</li>
      </ul>
    </div>
</template>

<script>
    export default {
        name: "test",
        data:function () {
          return{
            title:"hello vue.js!",
            user:{
              firstname:"paoy",
              lastname:"Zhang"
            },
            showName:true,
            items:[
              {title:"item1"},
              {title:"item2"},
              {title:"item3"},
              {title:"item4"}
            ]
          }
        }
    }
</script>

<style scoped>

</style>
