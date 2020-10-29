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
import { mapState } from "vuex";
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

  async fetch({ store, error }) {
    try {
      await store.dispatch("events/fetchEvents");
    } catch (e) {
      error({
        statusCode: 503,
        message: "Unable to fetch events events at this time",
      });
    }
  },
  computed: {
    ...mapState({
      events: (store) => store.events.events,
    }),
  },
};
</script>

 