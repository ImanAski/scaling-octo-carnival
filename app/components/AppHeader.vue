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
    label: 'وبلاگ',
    to: '/blog',
    active: route.path.startsWith('/blog')
  },
  {
    label: 'درباره ما',
    to: '/about',
    active: route.path.startsWith('/about')
  },
  {
    label: 'تماس با ما',
    to: '/contact',
    active: route.path.startsWith('/contact')
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
      <UIcon name="cart" />
      <UDrawer direction="left">
        <UButton>
          ورود
        </UButton>

      </UDrawer>
    </template>
  </UHeader>
</template>
