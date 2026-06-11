<script setup>
import { computed } from 'vue'

const props = defineProps({
  avatar: {
    type: String,
    required: true,
  },
  fullName: {
    type: String,
    required: true,
  },
  email: {
    type: String,
    required: true,
  },
  batch: {
    type: String,
    required: true,
  },
  track: {
    type: String,
    required: true,
  },
})

const initials = computed(() =>
  props.fullName
    .split(/\s+/)
    .filter(Boolean)
    .map((part) => part[0])
    .join('')
    .slice(0, 2)
    .toUpperCase(),
)
</script>

<template>
  <article class="profile-card profile-card--dark panel">
    <div class="profile-card__wrap">
      <div class="profile-card__topline">
        <p class="section-kicker">Student Profile</p>
        <span class="profile-card__status">Active Learner</span>
      </div>

      <div class="profile-card__hero">
        <div class="profile-card__avatar-wrap" :aria-label="`${fullName} avatar`">
          <span class="profile-card__avatar-initials" aria-hidden="true">{{ initials }}</span>
        </div>

        <div class="profile-card__copy">
          <h2>{{ fullName }}</h2>
          <p class="profile-card__email">{{ email }}</p>
        </div>
      </div>

      <dl class="profile-card__meta">
        <div>
          <div class="profile-card__meta-icon" aria-hidden="true">
            <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <rect x="3" y="4" width="18" height="18" rx="2"/>
              <path d="M16 2v4M8 2v4M3 10h18"/>
            </svg>
          </div>
          <div class="profile-card__meta-text">
            <dt>Batch</dt>
            <dd>{{ batch }}</dd>
          </div>
        </div>
        <div>
          <div class="profile-card__meta-icon" aria-hidden="true">
            <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <polyline points="16 18 22 12 16 6"/>
              <polyline points="8 6 2 12 8 18"/>
            </svg>
          </div>
          <div class="profile-card__meta-text">
            <dt>Track</dt>
            <dd>{{ track }}</dd>
          </div>
        </div>
      </dl>
    </div>
  </article>
</template>
