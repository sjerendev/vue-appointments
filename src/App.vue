<template>
  <div id="main-app" class="container">
    <div class="row justify-content-center">
      <appointment-list :appointments="appointments"></appointment-list>
    </div>
  </div>
</template>

<script>
import AppointmentList from "./components/AppointmentList.vue";
import axios from "axios";
export default {
  name: "MainApp",
  data: function () {
    return {
      title: "Appointment list",
      appointments: [],
    };
  },
  components: {
    AppointmentList,
  },
  mounted() {
    axios
      .get("./data/appointments.json")
      .then((response) => {
        this.appointments = response.data;
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>
