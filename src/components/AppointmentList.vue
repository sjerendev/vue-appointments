<template>
  <div class="col-12 col-md-10 col-lg-7">
    <div class="list-group list-group-flush">
      <div
        class="list-group-item d-flex align-items-start"
        v-for="(item, i) in appointments"
        v-bind:key="i"
      >
        <button class="me-2 btn btn-sm btn-danger">
          <font-awesome-icon icon="trash" />
        </button>
        <div class="w-100">
          <div class="d-flex justify-content-between">
            <span class="h4 text-primary">{{ item.petName }}</span>
            <span class="float-right">{{ formattedDate(item.aptDate) }}</span>
          </div>
          <div class="owner-name">
            <span class="fw-bold text-primary me-1">Ägare:</span>
            <span>{{ item.petOwner }}</span>
          </div>
          <div>{{ item.aptNotes }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import moment from "moment";
export default {
  name: "AppointmentList",
  props: ["appointments"],
  components: {
    FontAwesomeIcon,
  },
  methods: {
    formattedDate(date) {
      moment.locale("sv");
      return moment(new Date(date)).format("llll");
    },
  },
};
</script>
