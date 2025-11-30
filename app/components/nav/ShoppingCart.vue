<script setup lang="ts">
import { createReusableTemplate, useMediaQuery } from '@vueuse/core';

const [DefineFormTemplate, ReuseFormTemplate] = createReusableTemplate();

const isDesktop = useMediaQuery('(min-width: 768px)');

const open = ref<boolean>(false);

const title = "سبد خرید";

const cartItems = ref<any[]>([
  { name: "Test" },
  { name: "Test" },
  { name: "Test" },
  { name: "Test" },
  { name: "Test" },
  { name: "Test" },
  { name: "Test" },
  { name: "Test" },
  { name: "Test" },
  { name: "Test" },
  { name: "Test" },
]);

</script>

<template>
  <DefineFormTemplate>
    <div class="flex flex-col min-w-96 size-full gap-2">
      <div v-if="cartItems.length != 0">
        <div v-for="item in cartItems" class="flex flex-col mb-2">
          <div class="size-full flex justify-start items-center p-2">
            <span>{{ item.name }}</span>
          </div>
        </div>
      </div>
      <div v-else>
        <span>موردی برای نمایش وجود ندارد</span>
      </div>
    </div>
  </DefineFormTemplate>

  <UModal v-if="isDesktop" v-model:open="open" :title="title">
    <UButton icon="i-lucide-shopping-cart" variant="link" color="#fff" />

    <template #body>
      <ReuseFormTemplate />
    </template>
  </UModal>

  <UDrawer v-else v-model:open="open" :title="title">
    <UButton icon="i-lucide-shopping-cart" variant="link" color="#fff" />

    <template #body>
      <ReuseFormTemplate />
    </template>
  </UDrawer>


</template>
