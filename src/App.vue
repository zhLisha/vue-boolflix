<template>
  <div id="app">
    <!-- Header -->
    <header>
      <HeaderComp @getApi="apiMusic" />
    </header>

    <main>
      <MainComp :getUserChoose="userChoose"/>
    </main>
  </div>
</template>

<script>
import MainComp from './components/MainComp.vue'
import HeaderComp from './components/HeaderComp.vue'


export default {
  name: 'App',
  components: {
    MainComp,
    HeaderComp
  },

  data() {
    return {
      userChoose: '',
    }
  },

  methods: {
    apiMusic(show){
      this.userChoose = show;
    }
  },

  created() {
    this.apiMusic
  }

}
</script>

<style lang="scss">
@import './style/common.scss';
@import './style/variables.scss';

</style>
