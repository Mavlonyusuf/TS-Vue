<template>
  <div class="bg-dark d-flex flex-column p-5">
    <div
      class="btn-group container"
      role="group"
      aria-label="Basic outlined example container-sm"
      style="width: 16rem"
    >
      <button
        type="button"
        @click="clickHandler('title')"
        class="btn btn-outline-primary"
      >
        Title
      </button>
      <button
        type="button"
        @click="clickHandler('salary')"
        class="btn btn-outline-primary"
      >
        Salary
      </button>
      <button
        type="button"
        @click="clickHandler('location')"
        class="btn btn-outline-primary"
      >
        Location
      </button>
    </div>
    <div class="mx-auto pt-5">
      <h4 class="text-success">Filter by {{ order }}</h4>
    </div>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import JobList from "./components/JobList.vue";
import Job from "./types/Job";
import OrderTerm from "./types/OrderTerm";
export default defineComponent({
  name: "App",
  components: {
    JobList,
  },
  setup() {
    const jobs = ref<Job[]>([
      {
        title: "Front-end Developer",
        location: "Tashkent",
        salary: 2000,
        id: 1,
      },
      {
        title: "Mobile Developer",
        location: "Piter",
        salary: 1500,
        id: 2,
      },
      {
        title: "Full-Stack Developer",
        location: "Moscow",
        salary: 4000,
        id: 3,
      },
      {
        title: "Back-end Developer",
        location: "Washington",
        salary: 5000,
        id: 4,
      },
    ]);
    const order = ref<OrderTerm>("title");
    const clickHandler = (term: OrderTerm) => {
      order.value = term;
    };

    return {
      jobs,
      order,
      clickHandler,
    };
  },
});
</script>

<style></style>
