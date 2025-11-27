<script setup lang="ts">
import type { NavigationMenuItem } from '@nuxt/ui'

const route = useRoute()

const items = computed<NavigationMenuItem[]>(() => [
  {
    label: 'فروشگاه',
    to: '/products',
    active: route.path.startsWith('/products')
  },
  {
    label: 'دسته بندی',
    to: '/docs/components',
    active: route.path.startsWith('/docs/components')
  },
  {
    label: 'درباره ما',
    to: '/about',
  },
  {
    label: 'تماس با ما',
    to: '/contact',
  }
])
</script>

<template>
  <UHeader>
    <template #title>
      <Logo class="h-6 w-auto" />
    </template>

    <UNavigationMenu :items="items" />

    <template #right>
      <UColorModeButton />
      <UContentSearchButton />
    </template>
  </UHeader>
</template>
