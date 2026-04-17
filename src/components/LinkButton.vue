<script setup lang="ts">
defineProps<{
  label: string
  url: string
  icon: string
}>()
</script>

<template>
  <v-btn
    :href="url"
    target="_blank"
    rel="noopener noreferrer"
    size="large"
    variant="elevated"
    color="primary"
    block
    rounded="lg"
  >
    <v-icon start>{{ icon }}</v-icon>
    {{ label }}
  </v-btn>
</template>
