<script setup>
import { computed } from 'vue'

const props = defineProps({
  title: {
    type: String,
    required: true,
  },
  dueDate: {
    type: String,
    required: true,
  },
  status: {
    type: String,
    required: true,
    validator: (value) => ['pending', 'completed'].includes(value),
  },
})

const statusMeta = {
  completed: {
    label: 'Completed',
    icon: '✔',
  },
  pending: {
    label: 'Pending',
    icon: '•',
  },
}

const currentStatus = computed(() => statusMeta[props.status] ?? statusMeta.pending)
</script>

<template>
  <article class="assignment-card" :class="`is-${status}`">
    <div class="assignment-card__icon" aria-hidden="true">
      {{ currentStatus.icon }}
    </div>

    <div class="assignment-card__body">
      <h3>{{ title }}</h3>
      <p class="assignment-card__due">Due {{ dueDate }}</p>
    </div>

    <span class="assignment-card__status">
      {{ currentStatus.label }}
    </span>
  </article>
</template>
