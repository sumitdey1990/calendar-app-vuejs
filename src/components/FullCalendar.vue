<script>
import FullCalendar from '@fullcalendar/vue'
import dayGridPlugin from '@fullcalendar/daygrid'
import jsonData from './json-data.json'

export default {
  components: {
    FullCalendar 
  },
  data: function() {
    return {
      calendarOptions: {
         plugins: [
          dayGridPlugin,
        ],
        initialView: 'dayGridMonth',
        initialEvents: jsonData,
      }
    }
  },
}
</script>

<template>
  <div class='calendar-app'>
    <div class='calendar-app-main'>
      <FullCalendar :options='calendarOptions'>
        <template v-slot:eventContent='arg'>
          <div class="text-center">
            <div class="sales-roundoff">
              <p v-if="arg.event.extendedProps.sales">Sales: {{ arg.event.extendedProps.sales }}</p>
              <p v-if="arg.event.extendedProps.roundoff">Round off: {{ arg.event.extendedProps.roundoff }}</p>
            </div>
            <img src="../assets/icon.png" height="30" /> 
            <p>{{ arg.event.extendedProps.temprature }}</p>
          </div>
        </template>
      </FullCalendar>
    </div>
  </div>
</template>

<style lang='css'>

.calendar-app {
  display: flex;
  min-height: 100%;
  font-family: Arial, Helvetica Neue, Helvetica, sans-serif;
  font-size: 14px;
}
.calendar-app-main {
  flex-grow: 1;
  padding: 1em 3em;
}
.fc-h-event {
  background: transparent;
  border: 0;
  color: #333;
}
.fc-h-event .fc-event-main {
  color: #333;
  padding-top: 60px;
}
.fc-h-event .fc-event-main p {
  margin: 0;
  font-weight: 600;
  font-size: 16px;
  color: rgba(0,0,0,0.6);
}
.text-center {
  text-align: center;
}
.fc-day-other img, .fc-day-other p{
  opacity: 0.3;
}
.fc .fc-daygrid-day-top a {
  font-size: 16px;
  font-weight: 600;
}
.fc .fc-daygrid-day-top {
  flex-direction: inherit;
}
.fc-h-event .fc-event-main .sales-roundoff {
  position: absolute;
  right: 0;
  top: -25px;
  text-align: right;
}
.fc .fc-daygrid-body-balanced .fc-daygrid-day-events {
  position: static;
  flex: 1;
}
.fc-h-event .fc-event-main .sales-roundoff p {
  font-size: 13px;
  font-weight: 400;
  color: #0000FF
}
.fc .fc-daygrid-day-frame {
  display: flex;
  flex-direction: column;
  height: 160px;
}
</style>
