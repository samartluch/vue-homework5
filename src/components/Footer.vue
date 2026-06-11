<script setup>
const props = defineProps({
  note: {
    type: String,
    default: 'Parent-to-child data flow with props',
  },
})

const year = new Date().getFullYear()
</script>

<template>
  <footer class="site-footer panel">
    <div class="site-footer__copy">
      <p class="site-footer__label">Vue 3 Composition API</p>
      <p class="site-footer__note">{{ props.note }}</p>
    </div>

    <div class="site-footer__chips">
      <span>Props</span>
      <span>Loops</span>
      <span>Responsive</span>
      <span>© {{ year }}</span>
    </div>
  </footer>
</template>
