<script setup lang="ts">
import { fa_ir } from "@nuxt/ui/locale";

useHead({
  htmlAttrs: {
    lang: fa_ir.code,
    dir: fa_ir.dir
  }
})
</script>

<template>
  <UApp :locale="fa_ir">
    <div>
      <NuxtRouteAnnouncer />
      <NuxtLayout>
        <NuxtPage />
      </NuxtLayout>
    </div>
  </UApp>
</template>

<style>
.page-enter-active,
.page-leave-active {
  transition: all 0.4s;
}

.page-enter-from,
.page-leave-to {
  opacity: 0;
  filter: blur(1rem);
}
</style>
