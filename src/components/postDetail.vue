<template>
    <div>
      <div>
        <h2>
          {{post.title}}
        </h2>
      </div>
      <div class="info">
        <ul>
          <div>Info:</div>
          <li>
            Theme - {{post.theme}}
          </li>
          <li>
            <ul>
              likes:
              <li>+ {{post.like.good}}</li>
              <li>- {{post.like.bad}}</li>
            </ul>
          </li>
          <li>
            Autor {{post.autor}}
          </li>
          <li>
            date {{post.date}}
          </li>
        </ul>
      </div>
      <div class="swiper-container">
        <swiper :options="swiperOption" ref="mySwiper">
          <swiper-slide v-for='imgScr in post.img' :key="Math.random()">
            <img v-bind:src="imgScr" alt="no found"/>
          </swiper-slide>
          <div class="swiper-pagination"  slot="pagination"></div>
          <div class="swiper-button-prev" slot="button-prev"></div>
          <div class="swiper-button-next" slot="button-next"></div>
          <div class="swiper-scrollbar" slot="scrollbar"></div>
        </swiper> 
      </div>
      <p class="text">
        {{post.text}}
      </p>
    </div>
</template>

<script>
import Data from '../data.js';
export default {
  name: 'postDetail',
  data () {
    return {
      post: "",
      swiperOption: {
        notNextTick: true,
        autoplay: 3000,
        direction : 'vertical',
        grabCursor : true,
        setWrapperSize :true,
        autoHeight: true,
        pagination : '.swiper-pagination',
        paginationClickable :true,
        prevButton:'.swiper-button-prev',
        nextButton:'.swiper-button-next',
        scrollbar:'.swiper-scrollbar',
        mousewheelControl : true,
        observeParents:true,
        debugger: true
      }
    }
  },
  created() {
    console.log(Data.getHash());
    if ("" + Data.getHash() !== "NaN") {
      this.post = {
        id: "",
        title: "POST NOT FOUND",
        text: ""
      }
      for (var j = 0; j < Data.posts.length; j++) {
        if (Data.getHash() === Data.posts[j].id) {
          this.post = Data.posts[j];
          return;
        }
      }
    }
    

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass" scoped>
h2
  font-size: 26px
  text-align: center
  padding: 32px
  font-style: oblique
  font-weight: 900
.info
  font-size: 20px
  padding: 25px
  max-width: 600px
  border-bottom: 1px solid #CCC
  ul 
    div
      text-align: center
      padding-bottom: 10px
      font-size: 22px
      font-weight: 600
    ul li
      padding-left: 15px
.swiper-container
  margin-top: 20px
  border: 0px solid black
  height: 200px
  .swiper-slide
    height: 200px !important
    width: 200px
    margin: auto
  .swiper-wrapper
    height: 200px
    width: 200px
    margin: auto
  img
    height: 150px
  .swiper-button-prev
    transform: translateX(500%)
  .swiper-button-next
    transform: translateX(-500%)
  .swiper-scrollbar
    display: none
.text
  font-size: 22px
  padding: 10px
</style>
