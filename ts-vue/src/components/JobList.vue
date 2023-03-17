<template>
  <div class="container">
    <transition-group class="list-group" name="list" tag="ul">
      <li
        class="list-group-item m-4 bg-secondary text-white rounded border border-primary"
        v-for="job in orderedJob"
        :key="job.id"
      >
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
          <p class="text-danger">${{ job.salary }}</p>
        </div>
        <div class="description">
          <p>
            Lorem ipsum dolor sit, amet consectetur adipisicing elit. Ut
            pariatur dolore facilis. Quo rem deleniti beatae consequuntur
            possimus explicabo ipsum dolore assumenda! In quidem deserunt
            voluptates iure earum molestias ducimus!
          </p>
        </div>
      </li>
    </transition-group>
  </div>
</template>

<style scoped>
.list-move {
  transition: all 0.7s ease-in-out;
}
</style>
<script lang="ts">
import { computed, defineComponent, PropType } from "vue";
import Job from "../types/Job";
import OrderTerm from "../types/OrderTerm";
export default defineComponent({
  props: {
    jobs: {
      required: true,
      type: Array as PropType<Job[]>,
    },
    order: {
      required: true,
      type: String as PropType<OrderTerm>,
    },
  },
  setup(props) {
    const orderedJob = computed(() => {
      return [...props.jobs].sort((a: Job, b: Job) => {
        return a[props.order] > b[props.order] ? 1 : -1;
      });
    });

    return {
      orderedJob,
    };
  },
});
</script>
