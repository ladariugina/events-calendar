<template>
  <div id="calendar"></div>
</template>

<script>
import moment from "moment";
import AirDatepicker from "air-datepicker";

export default {
  props: {
    events: Array,
  },
  data() {
    return {
      datepicker: null,
      daysWeek: [
        "Воскресенье",
        "Понедельник",
        "Вторник",
        "Среда",
        "Четверг",
        "Пятница",
        "Суббота",
      ],
    };
  },
  mounted() {
    const self = this;
    this.datepicker = new AirDatepicker("#calendar", {
      inline: true,
      navTitles: {
        days: "MMMM",
      },
      locale: {
        daysMin: this.daysWeek,
      },
      onRenderCell({ date }) {
        return {
          classes: self.isDatePastDay(date),
          html: self.getRenderDayTemplate(date),
        };
      },
      onChangeViewDate: ({ year }) => {
        this.datepicker.update({
          navTitles: {
            days: self.getNavTitles(year),
          },
        });
      },
    });
  },
  methods: {
    getRenderDayTemplate(date) {
      const day = moment(date).date();
      const formattedDate = moment(date).format("YYYY-MM-DD");
      const dateEvents = this.events.filter((event) => event.date === formattedDate);
      const html = [`<div class="calendar-day">${day}</div>`];

      dateEvents.forEach((item) =>
        html.push(
          `<div class="calendar-event calendar-event--${item.type}">${item.name}</div>`
        )
      );

      if (dateEvents) return html.join("\n");
    },
    isDatePastDay(date) {
      const today = moment().format("YYYY-MM-DD");
      if (moment(today).isAfter(date)) return "past-day";
    },
    getNavTitles(year) {
      const currentYear = moment().year();
      let daysTemplate = "";

      if (currentYear !== year) daysTemplate = "MMMM yyyy";
      else daysTemplate = "MMMM";

      return daysTemplate;
    },
  },
};
</script>
