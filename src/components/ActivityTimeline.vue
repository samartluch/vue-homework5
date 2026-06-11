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
        <p class="section-kicker">Recent Activities</p>
        <h2 id="timeline-heading">Activity Log</h2>
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

    <div class="timeline-panel__footer" role="button" tabindex="0">
      View full timeline
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
        <path d="M5 12h14M13 6l6 6-6 6"/>
      </svg>
    </div>
  </section>
</template>
