<template>
  <div id="app">
    <navbar></navbar>
    <nuxt />
  </div>
</template>


<script>
import navbar from "~/components/NavBar";
export default {
  head() {
    return {
      titleTemplate: "%s - Real World Events",
      meta: [
        {
          hid: "description",
          name: "description",
          content:
            "Where you can find all the events taking place in your neighborhood",
        },
      ],
    };
  },
  components: {
    navbar,
  },
};
</script>