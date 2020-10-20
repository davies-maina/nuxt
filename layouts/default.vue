<template>
  <div id="app">
    <navbar></navbar>
    <nuxt/>
  </div>
</template>


<script>
import navbar from '~/components/NavBar';
export default {
  components:{
    navbar
  }
}
</script>