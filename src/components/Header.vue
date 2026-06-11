<script setup>
import { computed } from 'vue'

const props = defineProps({
  brand: {
    type: String,
    required: true,
  },
  title: {
    type: String,
    required: true,
  },
  studentName: {
    type: String,
    required: true,
  },
})

const brandMark = computed(() =>
  props.brand
    .split(/\s+/)
    .filter(Boolean)
    .map((part) => part[0])
    .join('')
    .slice(0, 2)
    .toUpperCase(),
)

const studentInitials = computed(() =>
  props.studentName
    .split(/\s+/)
    .filter(Boolean)
    .map((part) => part[0])
    .join('')
    .slice(0, 2)
    .toUpperCase(),
)
</script>

<template>
  <header class="site-header panel">
    <div class="site-header__brand">
      <div class="site-header__mark" aria-hidden="true">
        {{ brandMark }}
      </div>

      <div class="site-header__copy">
        <p class="site-header__eyebrow">{{ brand }}</p>
        <h1 class="site-header__title">{{ title }}</h1>
        <p class="site-header__lede">
          Build reusable child components with a single parent data source.
        </p>
        <div class="site-header__subline" aria-label="Lab focus areas">
          <span>Composition API</span>
          <span>Props flow</span>
          <span>Responsive layout</span>
        </div>
      </div>
    </div>

    <div class="site-header__badge">
      <span class="site-header__badge-label">Live cohort</span>
      <div class="site-header__badge-row">
        <span class="site-header__badge-avatar" aria-hidden="true">
          {{ studentInitials }}
        </span>
        <div class="site-header__badge-copy">
          <strong class="site-header__badge-name">{{ studentName }}</strong>
          <span class="site-header__badge-note">Active learner</span>
        </div>
      </div>
    </div>
  </header>
</template>
