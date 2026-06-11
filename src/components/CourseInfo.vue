<script setup>
import { computed } from 'vue'

const props = defineProps({
  courseName: {
    type: String,
    required: true,
  },
  instructor: {
    type: String,
    required: true,
  },
  progress: {
    type: Number,
    required: true,
    validator: (value) => value >= 0 && value <= 100,
  },
})

const progressValue = computed(() => Math.max(0, Math.min(100, Number(props.progress) || 0)))
const progressRemaining = computed(() => 100 - progressValue.value)
const progressState = computed(() => {
  if (progressValue.value >= 80) {
    return 'Almost there'
  }

  if (progressValue.value >= 50) {
    return 'On track'
  }

  return 'Building momentum'
})
</script>

<template>
  <section class="course-info course-info--compact panel" aria-labelledby="course-info-heading">
    <div class="section-head section-head--compact">
      <div>
        <p class="section-kicker">Course Overview</p>
        <h2 id="course-info-heading">{{ courseName }}</h2>
      </div>
      <p class="section-summary">Progress, instructor context, and a live readiness meter.</p>
    </div>

    <div class="course-info__body">
      <div class="course-info__copy">
        <div class="course-info__meta">
          <p>
            <span class="course-info__label">Course</span>
            <span>{{ courseName }}</span>
          </p>
          <p>
            <span class="course-info__label">Instructor</span>
            <span>{{ instructor }}</span>
          </p>
        </div>

        <div class="course-info__progress">
          <div class="course-info__progress-head">
            <span class="course-info__label">Progress</span>
            <strong>{{ progressValue }}% complete</strong>
          </div>
          <div class="course-info__track" :style="{ '--progress': `${progressValue}%` }">
            <span class="course-info__fill" />
          </div>
          <p class="course-info__footnote">
            {{ progressRemaining }}% remaining in the current learning sprint.
          </p>
        </div>
      </div>

      <aside class="course-info__gauge" aria-label="Progress status">
        <div class="course-info__ring" :style="{ '--progress': `${progressValue}%` }">
          <div class="course-info__ring-core">
            <strong>{{ progressValue }}%</strong>
            <span>Complete</span>
          </div>
        </div>

        <div class="course-info__signal">
          <p>Status</p>
          <strong>{{ progressState }}</strong>
        </div>
      </aside>
    </div>
  </section>
</template>