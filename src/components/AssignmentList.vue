<script setup>
import AssignmentCard from './AssignmentCard.vue'

defineProps({
  assignments: {
    type: Array,
    required: true,
  },
})
</script>

<template>
  <section class="assignment-list panel" aria-labelledby="assignments-heading">
    <div class="section-head">
      <div>
        <p class="section-kicker">Work Queue</p>
        <h2 id="assignments-heading">Upcoming Assignments</h2>
      </div>
      <p class="section-summary">{{ assignments.length }} items in the queue</p>
    </div>

    <div class="assignment-list__stack">
      <AssignmentCard
        v-for="assignment in assignments"
        :key="assignment.title"
        v-bind="assignment"
      />
    </div>

    <div class="assignment-list__footer" role="button" tabindex="0">
      View all assignments
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
        <path d="M5 12h14M13 6l6 6-6 6"/>
      </svg>
    </div>
  </section>
</template>
