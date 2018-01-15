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

      <!--v-on-->
      <button v-on:click="greet('hello everybody')">say Greeting</button>

      <!--键盘事件-->
      <input type="text" v-on:keyup="presskey" v-on:keyup.enter="enterHit" v-on:keyup.alt.enter="enterHitAlt">

      <hr>
      <!--computed计算属性-->
      <label>FirstName</label>
      <input type="text" v-model="user.firstname">
      <br>
      <label>LastName</label>
      <input type="text" v-model="user.lastname">
      <br>
      <h3>{{fullName}}</h3>

      <!--props属性-->
      <h2>{{msg}}</h2>


    </div>
</template>

<script>
    export default {
        name: "test",
      props:{
          msg:{
            type:String,
            default:"默认文字"
          }
      },
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
        },
        methods:{
          greet:function (greeting) {
            alert(greeting)
          },
          presskey:function () {
            console.log("pressing...")
          },
          enterHit:function () {
            console.log("you press enterkey")
          },
          enterHitAlt:function () {
            console.log("you press alt+enterkey")
          }
        },
        computed:{
          fullName:function () {
            return this.user.firstname+" "+this.user.lastname;
          }
        }
    }
</script>

<style scoped>

</style>
