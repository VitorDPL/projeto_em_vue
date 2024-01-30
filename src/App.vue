<template>
  <NavBar/>
  <body>

  </body>
  <Footer/>
</template>

<script>
import Banner from './components/Banner.vue';
import NavBar from './components/NavBar.vue';
import Footer from './components/Footer.vue';

export default {
  name: 'App',
  components: {
    Banner,
    NavBar,
    Footer
  }
}
</script>

<style>
  *{
    font-family: Helvetica, sans-serif;
    margin: 0px;
    padding: 0px;
  }

  body {
    background-color: #fcd8fc;
  }

</style>