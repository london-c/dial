<style>
  .profile {
    display: inline-block;
    vertical-align: top;
    margin-right: 20px;
    cursor: pointer;
    opacity: 1;
  }

  .profile:hover {
    opacity: 0.7;
  }

  .profile .img {
    width: 40px;
    height: 40px;
    display: inline-block;
    background: url(img/profile.png);
    background-position: center;
    background-size: 100%;
    border-radius: 50%;
    vertical-align: top;
    opacity: 0.6;
  }

  .profile .name {
    font-size: 4rem;
    display: inline-block;
    vertical-align: top;
    line-height: 4rem;
  }
</style>

<template>
  <div class="profile" v-on:click="openConf()">
    <div class="img"></div>
  </div>
  <configure-profile v-ref:configurator v-bind:config.sync="config"></configure-profile>
</template>

<script>

var Vue = require('vue');
var ConfigureProfile = require('./configure-profile.vue');

module.exports = Vue.extend({

  props: ["config"],

  components: {
    'configure-profile': ConfigureProfile
  },

  data: function(){
    return {
    };
  },

  methods: {
    openConf: function(){
      this.$refs.configurator.open();
    }
  }

});

</script>
