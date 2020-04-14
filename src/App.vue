<template>
  <div id="app" class="background">
    <a><br>
      <input v-model="newRower" type="text" align="center" v-on:keyup.enter="rower"> &emsp;
      <input type="submit" value="send" class="button" @click="rower2">
    </a>
    <ul id="">
      <li v-for="(item, index) in items" :key="item.id">
        <i class="fas fa-dog" style="color: #ff3d77"></i>
        <input type ="checkbox" v-model="item.done">
        <s v-if="item.done">
          {{index+1}} {{item.message}}
        </s>
        <span v-else>
          {{index+1}} {{item.message}}
        </span>
          <button @click="removeTodo(index)" class="button">delete</button>
      </li>


    </ul>
      <button @click="checkAll" class="button">select all</button>
    <marquee behavior="scroll" direction="left" bgcolor="E836A1" scrollamount="6"><strong style="font-size: 45px; color:#FFFFFF" >Лёша, смотри, у меня получилось!</strong></marquee>
  </div>
</template>

<script>
  // import HelloWorld from './components/HelloWorld.vue'
  var moment = require('moment');
  concole.log(moment().format());
  export default {
    name: 'App',
    components: {
// HelloWorld
    },
    data(){
      return{
        newRower:"",
        name1:"punkt 1",
        name2: "punkt 2",
        checkedAll: false,

// name2:"punkt 2",
        items:[
          { id:1, message: 'Client meeting @ 2:30pm', done: false},
          { id:2, message: 'Design app interface', done: false},
          { id:3, message:'Learn node.js', done: false}
        ]
      }
    },
    methods:{
      rower({target}){
        console.log(target.value);
      },
      rower2(  ){
        this.items.push({ id:Date.now(), message:this.newRower, done: false});
        this.newRower="";
    },
    removeTodo(index) {
      this.items.splice(index, 1);
    },
    checkAll() {
      for (var i = 0; i < this.items.length; i++) {
        this.items[i].done = !this.checkedAll;
      }
      this.checkedAll = !this.checkedAll;

    },
    itemChanged(index) {
      if(!this.items[index].done && this.checkedAll) this.checkedAll=!this.checkedAll;
      // !this.itemsa[index].complete&&this.checkedAll?this.checkedAll=!this.checkedAll:'';
      }
    }
  }
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Raleway:wght@200&display=swap');
  body {
  background-color: #61DBFB;
  font-family: 'Raleway', sans-serif;
    display: -webkit-box;
    display: flex;
    -webkit-box-pack: center;
    justify-content: center;
    -webkit-box-align: center;
    align-items: center
}
.background {
  background-color: #393F49;
  width: 1000px;
  height: 500px;
  margin: 0 auto;
  border-radius: 5px;
  -webkit-box-shadow: 10px 10px 8px -5px rgba(0,0,0,0.75);
  -moz-box-shadow: 10px 10px 8px -5px rgba(0,0,0,0.75);
  box-shadow: 10px 10px 8px -5px rgba(0,0,0,0.75);
}
   .button {
    width: 75px;
    height: 37px;
    font-size: 15px;
    text-align: center;
    line-height: 37px;
    color: rgba(255,255,255,0.9);
    border-radius: 50px;
    background: linear-gradient(-45deg, #ffa63d, #ff3d77, #338aff, #3cf0c5);
    background-size: 600%;
    -webkit-animation: anime 16s linear infinite;
    animation: anime 16s linear infinite;
  }
  .buttonq {
    position: absolute;
    margin-top: -70px;
    z-index: -1;
    -webkit-filter: blur(30px);
    filter: blur(30px);
    opacity: 0.8;
  }
  @-webkit-keyframes anime {
    0% {
      background-position: 0% 50%;
    }
    50% {
      background-position: 100% 50%;
    }
    100% {
      background-position: 0% 50%;
    }
  }
  @keyframes anime {
    0% {
      background-position: 0% 50%;
    }
    50% {
      background-position: 100% 50%;
    }
    100% {
      background-position: 0% 50%;
    }
  }
  #app {
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #f0f6ff;
    margin-top: 60px;
  }

</style>
