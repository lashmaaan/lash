<template>
  <div id="app" align="justify">
    <img alt="Vue logo" src="./assets/logo.png">

    <a><br>
      <input v-model="newRower" type="text" align="center" v-on:keyup.enter="rower"> &emsp;
      <input type="submit" value="send" @click="rower2">
    </a>
    <ul id="">
      <li v-for="(item, index) in items" :key="item.id">
        <input type ="checkbox" v-model="item.done">
        <s v-if="item.done">
          {{index}} {{item.message}}
        </s>
        <span v-else>
          {{index}} {{item.message}}
        </span>
      </li>


    </ul>
  </div>
</template>

<script>
  // import HelloWorld from './components/HelloWorld.vue'

  export default {
    name: 'App',
    components: {
// HelloWorld
    },
    data(){
      return{
        newRower:"",
        name2:"punkt 1",
// name2:"punkt 2",
        items:[
          { id:2, message: 'madrower', done: false},
          { id:1, message:'madrower2', done: true}
        ]

      }
    },
    methods:{
      rower({target}){
        console.log(target.value)
      },
      rower2(  ){
        this.items.push({ id:Date.now(), message:this.newRower}),
        this.newRower=""
      }
    }
  }
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
