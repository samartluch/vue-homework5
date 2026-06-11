<script setup>
defineProps({
  title: {
    type: String,
    required: true,
  },
  value: {
    type: [String, Number],
    required: true,
  },
  icon: {
    type: String,
    required: true,
  },
})
</script>

<template>
  <article class="stat-card">
    <div class="stat-card__icon" aria-hidden="true">
      <svg
        v-if="icon === 'book-open'"
        class="stat-card__svg"
        viewBox="0 0 24 24"
        fill="none"
      >
        <path
          d="M12 6.5c-1.6-1.2-3.6-1.8-5.8-1.8H4.7A1.7 1.7 0 0 0 3 6.4v10.5a1.7 1.7 0 0 0 1.7 1.7h1.5c2.2 0 4.2.6 5.8 1.8"
          stroke="currentColor"
          stroke-width="1.8"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
        <path
          d="M12 6.5c1.6-1.2 3.6-1.8 5.8-1.8h1.5A1.7 1.7 0 0 1 21 6.4v10.5a1.7 1.7 0 0 1-1.7 1.7h-1.5c-2.2 0-4.2.6-5.8 1.8"
          stroke="currentColor"
          stroke-width="1.8"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
        <path
          d="M12 6.5v14"
          stroke="currentColor"
          stroke-width="1.8"
          stroke-linecap="round"
        />
      </svg>

      <svg
        v-else-if="icon === 'check-circle'"
        class="stat-card__svg"
        viewBox="0 0 24 24"
        fill="none"
      >
        <circle cx="12" cy="12" r="8.25" stroke="currentColor" stroke-width="1.8" />
        <path
          d="m8.8 12.2 2.1 2.1 4.5-5.1"
          stroke="currentColor"
          stroke-width="1.8"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
      </svg>

      <svg
        v-else-if="icon === 'chart-line'"
        class="stat-card__svg"
        viewBox="0 0 24 24"
        fill="none"
      >
        <path d="M5 17h14" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" />
        <path
          d="M7.5 15.2 10.7 12 13 14.2 18 9.4"
          stroke="currentColor"
          stroke-width="1.8"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
        <path d="M17 9.4h1.4V10.8" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" />
      </svg>

      <svg v-else class="stat-card__svg" viewBox="0 0 24 24" fill="none">
        <circle cx="9" cy="9" r="2.8" stroke="currentColor" stroke-width="1.8" />
        <path
          d="M4.8 18.2c.7-2.4 2.6-3.8 4.2-3.8s3.6 1.4 4.2 3.8"
          stroke="currentColor"
          stroke-width="1.8"
          stroke-linecap="round"
        />
        <circle cx="16.6" cy="10.5" r="2" stroke="currentColor" stroke-width="1.8" />
        <path
          d="M14 18.2c.4-1.5 1.7-2.6 3-2.6s2.6 1.1 3 2.6"
          stroke="currentColor"
          stroke-width="1.8"
          stroke-linecap="round"
        />
      </svg>
    </div>
    <div class="stat-card__content">
      <p class="stat-card__title">{{ title }}</p>
      <p class="stat-card__value">{{ value }}</p>
    </div>
  </article>
</template>
