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
        <div>
          <p class="section-kicker">Student Profile</p>
          <h2>{{ fullName }}</h2>
        </div>
        <span class="profile-card__status">Active learner</span>
      </div>

      <div class="profile-card__hero">
        <div class="profile-card__avatar-wrap">
          <img
            class="profile-card__avatar"
            :src="avatar"
            :alt="`${fullName} avatar`"
            loading="lazy"
          />
        </div>

        <div class="profile-card__copy">
          <p class="profile-card__email">
            <span class="profile-card__email-icon" aria-hidden="true">{{ initials }}</span>
            {{ email }}
          </p>

          <dl class="profile-card__meta">
            <div>
              <dt>Batch</dt>
              <dd>{{ batch }}</dd>
            </div>
            <div>
              <dt>Track</dt>
              <dd>{{ track }}</dd>
            </div>
          </dl>
        </div>
      </div>
    </div>
  </article>
</template>