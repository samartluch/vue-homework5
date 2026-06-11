<script setup>
import ActivityItem from './ActivityItem.vue'

defineProps({
  activities: {
    type: Array,
    required: true,
  },
})
</script>

<template>
  <section class="timeline-panel panel" aria-labelledby="timeline-heading">
    <div class="section-head">
      <div>
        <p class="section-kicker">History</p>
        <h2 id="timeline-heading">Recent Activities</h2>
      </div>
      <p class="section-summary">The latest actions from the learning timeline.</p>
    </div>

    <div class="timeline-panel__list">
      <ActivityItem
        v-for="activity in activities"
        :key="`${activity.activityName}-${activity.date}`"
        v-bind="activity"
      />
    </div>
  </section>
</template>
