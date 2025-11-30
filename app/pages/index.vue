<script setup lang="ts">
const links = ref([
  {
    label: 'Get started',
    to: '/docs/getting-started',
    icon: 'i-lucide-square-play'
  },
  {
    label: 'Learn more',
    to: '/docs/getting-started/theme/design-system',
    color: 'neutral',
    variant: 'subtle',
    trailingIcon: 'i-lucide-arrow-right'
  }
]);

const items = [
  'https://picsum.photos/640/640?random=1',
  'https://picsum.photos/640/640?random=2',
  'https://picsum.photos/640/640?random=3',
  'https://picsum.photos/640/640?random=4',
  'https://picsum.photos/640/640?random=5',
  'https://picsum.photos/640/640?random=6'
]
</script>


<template>
  <UContainer>
    <div class="flex flex-col">
      <!-- Main Header --->
      <UPageHero title="Ultimate Vue UI library"
        description="A Nuxt/Vue-integrated UI library providing a rich set of fully-styled, accessible and highly customizable components for building modern web applications."
        :links="links" />
    </div>

    <!-- New Arrivals --->
    <UPageCard title="محصولات جدید">

      <UCarousel v-slot="{ item }" dots :items="items" :ui="{ item: 'basis-1/5' }">
        <img :src="item" width="320" height="320" class="rounded-lg">
      </UCarousel>
    </UPageCard>

  </UContainer>
</template>
