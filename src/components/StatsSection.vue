<script setup>
import StatCard from './StatCard.vue'

defineProps({
  stats: {
    type: Array,
    required: true,
  },
})
</script>

<template>
  <section class="stats-section panel" aria-labelledby="stats-heading">
    <div class="section-head">
      <div>
        <p class="section-kicker">Tracking</p>
        <h2 id="stats-heading">Learning Stats</h2>
      </div>
      <p class="section-summary">Four quick metrics for the learner dashboard.</p>
    </div>

    <div class="stats-section__grid">
      <StatCard
        v-for="(stat, index) in stats"
        :key="stat.title"
        v-bind="stat"
        :class="`stat-card--tone-${index % 4}`"
      />
    </div>
  </section>
</template>
