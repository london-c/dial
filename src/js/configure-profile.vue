<style>

  .configure-window .clock_formats .clock_format {
    font-size: 3rem;
    float: left;
    display: inline-block;
  }

  .configure-window .clock_formats .format24 {
    margin-left: 20px;
  }


</style>

<template>
  <div v-el:modal class="configure-modal modal">
    <div class="configure-window window">
      <div class="close-btn" v-on:click="close()"></div>
      <h1 class="title">{{ $t('profile.profile') | uppercase }}</h1>
      <hr>
      <div class="row">
        <label for="config_profile_lang">{{ $t('profile.language') | uppercase }} <p class="config_note">{{$t('main.reload_required')}}</p></label>
        <select name="config_profile_lang" id="config_profile_lang" v-model="configTmp.profile.language">
          <option v-for="lang in config.profile.languages" value="{{lang.code}}">{{lang.name}}</option>
        </select>
      </div>
      <div class="row">
        <label for="config_profile_font">{{ $t('profile.font') | uppercase }}</label>
        <select name="config_profile_font" id="config_profile_font" v-model="configTmp.profile.font">
          <option v-for="(index, font) in config.profile.fonts" value="{{index}}">{{font.name}}</option>
        </select>
      </div>
      <div class="row save">
        <button class="btn config_save" v-on:click="save()">{{ $t('main.save') | uppercase }}</button>
      </div>
    </div>
  </div>
</template>

<script>

var Vue = require('vue');

module.exports = Vue.extend({

props: ["config"],

data: function(){
  return {
    configTmp: {
      profile: {
        language: this.config.profile.language,
        font: this.config.profile.font
      }
    }
  };
},

methods: {
  open: function(){
    this.$els.modal.classList.add('on');
  },
  save: function(){
    this.config.profile.language = this.configTmp.profile.language;
    this.config.profile.font = this.configTmp.profile.font;
    this.close();
  },
  close: function(){
    this.configTmp.profile.language = this.config.profile.language;
    this.$els.modal.classList.remove('on');
  }
}

});

</script>
