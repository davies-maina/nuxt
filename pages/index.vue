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

  asyncData(context, error) {
    return context.$axios
      .get("http://localhost:8000/events")
      .then((res) => {
        return {
          events: res.data,
        };
      })
      .catch((e) => {
        error({
          statusCode: 503,
          message: "unable to fetch events at this time. Please try again",
        });
      });
  },
  components: {
    EventCard,
  },
};
</script>

