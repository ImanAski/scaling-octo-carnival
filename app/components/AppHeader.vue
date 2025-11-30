<script setup lang="ts">
import type { NavigationMenuItem } from '@nuxt/ui'

const route = useRoute()

const searchQuery = ref<string | null>(null);

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
  <UHeader mode="slideover">
    <UFieldGroup>
      <UInput class="max-w-6xl" placeholder="جستجو" v-model="searchQuery" />
      <UButton icon="i-lucide-search" variant="outline">جستجو</UButton>
    </UFieldGroup>

    <template #content>
      <UNavigationMenu :items="items" orientation="vertical" />
    </template>

    <template #right>
      <NavSearch />

      <NavShoppingCart />

      <UColorModeButton />

      <NavAuth />
    </template>

    <template #body>
      <UNavigationMenu :items="items" orientation="vertical" />
    </template>
  </UHeader>
</template>
