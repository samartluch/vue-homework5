<script setup>
import { computed } from 'vue'

const props = defineProps({
  activityName: {
    type: String,
    required: true,
  },
  date: {
    type: String,
    required: true,
  },
  type: {
    type: String,
    required: true,
    validator: (value) => ['submit', 'quiz', 'unlock'].includes(value),
  },
})

const typeMeta = {
  submit: {
    label: 'Submission',
    icon: '↗',
  },
  quiz: {
    label: 'Quiz',
    icon: '?',
  },
  unlock: {
    label: 'Unlock',
    icon: '✦',
  },
}

const currentType = computed(() => typeMeta[props.type] ?? typeMeta.submit)
</script>

<template>
  <article class="activity-item" :class="`activity-item--${type}`">
    <div class="activity-item__marker" aria-hidden="true">
      {{ currentType.icon }}
    </div>

    <div class="activity-item__copy">
      <p class="activity-item__name">{{ activityName }}</p>
      <p class="activity-item__date">{{ date }}</p>
    </div>

    <span class="activity-item__type">{{ currentType.label }}</span>
  </article>
</template>
