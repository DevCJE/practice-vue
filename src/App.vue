<template>
  <div>
    <header>
      <Nav v-bind:my-message="parentMsg"/>
      <Header v-bind:my-message="parentMsg"/>
      <div>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <input v-model="parentMsg">
      </div>
    </header>
    <section>
      <div id="main" class="container">
        <router-view v-if="load"></router-view>
        <div v-else>
          <Error/> // 추가해주면 됩니다.
        </div>
      </div>
    </section>
  </div>
</template>

<script>
    import Header from './components/Header.vue'
    import Nav from './components/Nav.vue'

    export default {
        name: 'App',
        components: {
            Header,
            Nav
        },
        data: function(){
          return{
            load : true,
            parentMsg:''
          }
        },
        methods:{
          checkUnload: function () {
            var htmlLength = document.getElementById("main").innerHTML.length
            if(htmlLength == 7){
              this.load = false
              // alert('잘못된 접근 방식 입니다.')
              // window.location.href='/'
            }
          }
        },
      mounted: function () {
        this.checkUnload()
      }
    }
</script>

<style>
</style>
