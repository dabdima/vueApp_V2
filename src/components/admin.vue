<template>
  <div>
    <h1>
      {{title}}
    </h1>
    <div>
      {{id}} <br>
      <input placeholder="title" v-model="title"/> <br>
      <input placeholder="theme" v-model="theme"/> <br>
      <textarea placeholder="text" v-model="text"></textarea> <br>
      <input placeholder="autor" v-model="autor"/> <br>
      {{date}} <br>
      <input placeholder="img url" v-model="imgUrl"/><button>open list</button>
      <br>
      <button> add </button>
    </div>
  </div>
</template>

<script>
import Data from '../data.js';

export default {
  name: 'admin',
  data () {
    return {
      id: 0,
      title: "",
      theme: "",
      text: "",
      autor: "",
      imgUrl: "",
      title: 'Add Post',
      date: ""
    }
  },
  created (){
    var t = new Date();
    this.date = t.getFullYear() + "-" + t.getMonth() + "-" + t.getDate() + " " + t.getHours() + ":" + t.getMinutes();
    var maxId = 0;
    for (var i = 0; i < Data.posts.length; i++){
      if (maxId < Data.posts[i].id) {
        maxId = Data.posts[i].id;
      }
    }
    this.id = maxId + 1;
  },
  methods: {
    addPost: function () {

    }
  }
}
</script>

<style lang="sass" scoped>
h1
  width: calc(100vw - 50px)
  text-align: center
  padding: 25px
  font-size: 45px
</style>
