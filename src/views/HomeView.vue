<script setup lang="ts">
import { useTheme } from 'vuetify'
import LinkButton from '@/components/LinkButton.vue'

const theme = useTheme()

function toggleTheme() {
  theme.global.name.value = theme.global.current.value.dark ? 'light' : 'dark'
}

const links = [
  { label: 'Portfolio', url: 'https://example.com/portfolio', icon: 'mdi-palette' },
  { label: 'LinkedIn', url: 'https://linkedin.com', icon: 'mdi-linkedin' },
  { label: 'Email', url: 'mailto:nadia@example.com', icon: 'mdi-email' },
]
</script>

<template>
  <v-container class="fill-height" fluid>
    <v-row justify="center" align="center">
      <v-col cols="12" sm="8" md="5" lg="4">
        <v-card class="pa-8 text-center" rounded="xl" elevation="4">
          <v-btn
            icon
            variant="text"
            size="small"
            style="position: absolute; top: 12px; right: 12px;"
            :aria-label="theme.global.current.value.dark ? 'Switch to light mode' : 'Switch to dark mode'"
            @click="toggleTheme"
          >
            <v-icon>{{ theme.global.current.value.dark ? 'mdi-weather-sunny' : 'mdi-weather-night' }}</v-icon>
          </v-btn>

          <v-avatar size="100" class="mb-4" color="purple-accent-2">
            <span class="text-h4 font-weight-bold text-white">NM</span>
          </v-avatar>

          <h1 class="text-h5 font-weight-bold mb-1">Nadia Magenta</h1>
          <p class="text-body-2 text-medium-emphasis mb-6">Developer · Designer · Creator</p>

          <div class="d-flex flex-column ga-3">
            <LinkButton
              v-for="link in links"
              :key="link.label"
              :label="link.label"
              :url="link.url"
              :icon="link.icon"
            />
          </div>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>
