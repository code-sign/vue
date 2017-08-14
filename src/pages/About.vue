<template>
  <sub-layout>
    <p>About page</p>
    <p>{{msg}}</p>
    <input v-model="sameText" placeholder="입력해보세요">
    <p>{{sameText}}</p>

    <button @click="hello">view message</button>

    <hr>

    <input type="radio" id="rd1" v-model="tabs" value="v-a">
    <label for="rd1">First</label>
    <input type="radio" id="rd2" v-model="tabs" value="v-b">
    <label for="rd2">Second</label>

    <transition name="fade" mode="out-in">
      <component :is="tabs"></component>
    </transition>

    <hr>

    <div v-for="(item, index) in posts" class="flipper" v-bind:class="{'flip':item.flip}" @click="letsFlip(item)">

      <div class="front">
              {{index+1}}, {{item.name}}
      </div>
      <div class="back">
              {{item.text}}
      </div>
    </div>


  </sub-layout>
</template>

<style>
  /* 전체 transition enter, enter-to, leave, leave-to  */
  .fade-enter-active, .fade-leave-active{
    transition:all .3s ease-out;
  }

  /* 처음과 끝 */
  .fade-enter, .fade-leave-to{
    opacity:0;
    transform:translateY(20px);
  }

  .flipper{
    position:relative;
    display:inline-block;
    transition:all .3s ease-out;
    transform-style:preserve-3d;
    background:#ccc;
    margin:5px;
    text-align:center;
    padding:15px;
  }
  .flipper.flip{
    background:royalblue;
    color:#fff;
    transform:rotateY(180deg);
  }

  .front, .back{
    position:absolute;
    top:0;
    left:0;
    width:100%;
    height:100%;
    backface-visibility: hidden;
    background-color:#fff;
    color:#444;
  }

  .front{
    border:1px solid red;
  }

  .back{
    border:1px solid blue;
    transform:rotateY(180deg);
  }
</style>

<script>
  import SubLayout from '../layouts/Sub.vue'

  export default {
    components: {
      SubLayout,
      'v-a':{
        template:'<p>this is first-tab content</p>'
      },
      'v-b':{
        template:'<p>this is second-tab content</p>'
      }
    },
    data (){
      return {
        msg: 'hello!!!!',
        sameText:'',
        tabs:'v-a',
        posts:[
          {id:1, flip:false, text:'hi', name:'aaa'},
          {id:2, flip:false, text:'*', name:'bbb'},
          {id:3, flip:false, text:'bye', name:'ccc'}
        ]        
      }
    },
    created (){
      this.sameText = 'bye!'
    },
    methods:{
      hello: function(){
        alert('hi')
      },
      letsFlip: function(item){
        this.posts.filter(function(v){
          return v.id != item.id;
        }).forEach(function(v){
          v.flip = false;
        })
        window.setTimeout(function(v){
          item.flip = !item.flip;  
        }, 100)         
      }
    }
  }


</script>
