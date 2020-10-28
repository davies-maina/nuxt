<template>
  <div>
    <h1>Event #{{ event.title }}</h1>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: "Event #" + this.event.title,
      meta: [
        {
          hid: "description",
          name: "description",
          content: "What you need to know about event #" + this.event.title,
        },
      ],
    };
  },

  async asyncData({ $axios, error, params }) {
    try {
      const { data } = await $axios.get(
        "http://localhost:8000/events/" + params.id
      );
      return {
        event: data,
      };
    } catch (e) {
      error({
        statusCode: 503,
        message: "Unable to fetch this event" + params.id,
      });
    }
  },

  computed: {
    id() {
      return this.$route.params.id;
    },
  },
};
</script>