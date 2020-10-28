<template>
  <div>
    <h1>Events</h1>
    <EventCard
      v-for="(event, index) in events"
      :key="index"
      :event="event"
      :data-index="index"
    />
  </div>
</template>

<script>
import EventCard from "../components/EventCard";
export default {
  head() {
    // <-- property used by vue-meta to add header tags
    return {
      title: "Event Listing", // <-- For our title tag
    };
  },
  components: {
    EventCard,
  },

  async asyncData({ $axios, error }) {
    try {
      const { data } = await $axios.get("http://localhost:8000/events");
      return {
        events: data,
      };
    } catch (e) {
      error({
        statusCode: 503,
        message: "Unable to fetch events events at this time",
      });
    }
  },
};
</script>

 