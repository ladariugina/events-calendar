<template>
  <CalendarEvents :events="events" />
</template>

<script>
import CalendarEvents from "./components/CalendarEvents.vue";

export default {
  components: {
    CalendarEvents,
  },
  data() {
    return {
      events: [
        {
          id: 1,
          name: "14:00 Коммуникационный дизайн среды",
          date: "2022-04-10",
          type: "green",
        },
        {
          id: 2,
          name: "16:00 Семинар",
          date: "2022-04-10",
          type: "red",
        },
        {
          id: 3,
          name: "12:00 Коммуникационный дизайн среды",
          date: "2022-04-21",
          type: "orange",
        },
        {
          id: 4,
          name: "12:00 Занятие 1",
          date: "2022-04-11",
          type: "orange",
        },
        {
          id: 3,
          name: "12:00 Английский язык",
          date: "2022-04-16",
          type: "red",
        },
        {
          id: 4,
          name: "12:00 Немецкий язык",
          date: "2022-04-27",
          type: "green",
        },
        {
          id: 4,
          name: "16:00 Искусство",
          date: "2022-04-27",
          type: "red",
        },
      ],
    };
  },
};
</script>
