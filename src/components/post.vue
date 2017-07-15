<template>
    <div>
      <div class="filter-warapper">
        <input type="text" placeholder="key word" v-model="keyWord"/>
        <div class="sort-wrapper">
          <input name="sort" type="radio" value="ask" id="ask" v-model="direction"/>
          <label for="ask">
              Ascending
          </label>
          <input name="sort" type="radio" value="desc" id="desc" v-model="direction"/>
          <label for="desc">
              Descendingly
          </label>
        </div>
      </div>
      <ul>
        <li v-for="post in orderedPost">
          <div class="prev-post">
            <div class="poster">
              <img v-bind:src="post.img[0]" alt="no found"/>
            </div>
            <div class="info">
              <p class="title"> {{post.title}}</p>
              <p class="theme"> Theme : {{post.theme}}</p>
              <p class="autor"> Autor : {{post.autor}}</p>
              <div class="vote">
                <p> Up vote: </p>
                <div>
                  <button> + {{post.like.good}}</button>
                  <button> - {{post.like.good}}</button>
                </div>
              </div>
            </div>
            <div class="footer-post">
              <div>date create : {{post.date}}</div>
              <div>
                <router-link :to='{path : "/" + post.id}'>
                  <span>
                    More info...
                  </span>
                </router-link>
              </div>
            </div>
          </div>
        </li>
      </ul>
    </div>
</template>

<script>
import Data from '../data.js';

export default {
  name: 'post',
  data () {
    return {
      search : "id",
      direction: "desc", // asc //desk 
      keyWord: "",
      posts: {},
      filter : ""
    }
  },
  created() {
    this.posts = Data.posts;
  },
  computed: {
    orderedPost: function () {
      var list = [];
      if (this.keyWord !== "") {    
        for (var i = 0; i < this.posts.length; i++) {
          if (this.posts[i].title.indexOf(this.keyWord) + 1){
            list.push(this.posts[i]);
          }
        }
      } else {
        list = this.posts;
      }
      return _.orderBy(list, [this.search], [this.direction]);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass" scoped>
.filter-warapper
  max-width: calc(100vw - 60px)
  padding: 25px
  margin: 15px
  box-shadow: 0px 0px 10px 10px rgba(144, 144, 144, 1)
input[type=text]
  border: 1px solid
  width: 80%
  height: 30px
  transform: translateX(10%)
.sort-wrapper
  text-align: center
  padding: 10px
  margin-top: 15px
input[type=radio]
  display: none
  &:checked + label
    color: black
label
  
  font-size: 28px
  font-weight: 900
  color: #CCC
  cursor: pointer
  &[for=ask]:before
    content: '\\/ '
  &[for=desc]:before
    content: '/\\ '
  
.prev-post
  font-size: 20px
  width: calc(100% - 50px)
  border-bottom: 1px solid rgba(169, 169, 169, 0.6)
  padding: 25px
  display: flex
  flex-direction: row
  justify-content: space-around
  & > div
    max-width: 30%
    word-break: break-all
  .poster
      padding: 15px
      img
        width: auto
        min-width: 150px
        height: 150px

  & > div
    box-shadow: 0px 0px 10px 5px rgba(200, 200, 200, 1)
  & p
    padding: 5px 10px
  .title
    
    font-weight: 700
    font-size: 30px
    text-align: center
  .theme
    font-size: 25px
    font-style: oblique
  .autor
    text-decoration: underline
  .vote
    p, div
      text-align: center
    button
      width: 40% 
  .footer-post
    box-shadow: 0px 0px 0px 0px #FFF
    display: flex
    flex-direction: column
    justify-content: space-around
    div:first-child
      color: rgba(144, 144, 144, .5)
</style>
