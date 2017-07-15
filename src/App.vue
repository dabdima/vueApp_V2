<template>
  <div>
    <div class="header">
      <router-link to="/">
        <span
          v-on:click="setAnimate('home')">
          <img 
            src="./assets/logo.png"
            v-bind:class="{ active: link.home }" />
        </span>
      </router-link>
      <router-link to="/admin">                   
        <span
          v-bind:class="{ active: link.admin }"
          v-on:click="setAnimate('admin')">
          Admin panel
        </span>
      </router-link>
      <router-link to="/login">
        <span 
          v-on:click="setAnimate('login')"
          v-bind:class="{ active: link.login }">
          {{loginMsg}}
        </span>
      </router-link>
    </div>
    <div>
      <router-view></router-view>
    </div>
    <div class="footer">
    </div>
  </div>
</template>

<script>
import Data from './data.js';

export default {
  name: 'app',
  data (){
    return {
      loginMsg : "SING IN",
      link: {
        home : true,
        login: false,
        admin: false
      },
      f: false
    }
  },

  methods: {
    setAnimate: function (key) {
      for(var val in Object.keys(this.link)) {
        var key_all = Object.keys(this.link)[val];
        this.link[key_all] = false;
      }
      this.link[key] = true;
      console.log(key);
    },
    test : function(e) {
       e.preventDefault();
       this.f = !this.f;
    }

  }
}
</script>

<style lang="sass" scoped>

.header
  display: flex
  justify-content: space-around
  height: 100vw
  height: 100px
  background: rgba(169, 205, 205, 1)
  a
    display: flex
    flex-direction: column
    justify-content: center
    text-decoration: none
    font-size: 22px
    color: black
    &:hover
      text-decoration: underline
    &:active
      text-decoration: none
    
img
  width: 50px
  height: 50px

.active
  animation: pulse 1s infinite

@keyframes pulse
  0%
    -moz-box-shadow: 0 0 0 0 rgba(50, 115, 210, 1)
    box-shadow: 0 0 0 0 rgba(50, 115, 210,  1)  
  70%
    -moz-box-shadow: 0 0 0 9px rgba(50, 115, 210, 0)
    box-shadow: 0 0 0 9px rgba(50, 115, 210, 0)
  100% 
    -moz-box-shadow: 0 0 0 0 rgba(50, 115, 210, 0)
    box-shadow: 0 0 0 0 rgba(50, 115, 210, 0)

</style>
