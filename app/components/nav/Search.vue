<script setup lang="ts">

import { createReusableTemplate, useMediaQuery } from '@vueuse/core';

const [DefineFormTemplate, ReuseFormTemplate] = createReusableTemplate();

const isDesktop = useMediaQuery('(min-width: 768px)');

const open = ref<boolean>(false);

const searchQuery = ref<string>("");

const fetchedItems = ref<any[]>([]);
// const fetchedItems = ref<any[]>([
//   { name: "Test" },
//   { name: "Test" },
//   { name: "Test" },
//   { name: "Test" },
//   { name: "Test" },
//   { name: "Test" },
//   { name: "Test" },
//   { name: "Test" },
//   { name: "Test" },
//   { name: "Test" },
//   { name: "Test" },
// ]);

const handleSearch = () => {
  if (searchQuery.value == "") {
    return;
  }
}

const title = "جستجو";
</script>

<template>
  <DefineFormTemplate>
    <div class="size-full mx-auto h-96 max-h-96 flex flex-col gap-4">
      <UFieldGroup class="w-full flex justify-center">
        <UInput class="flex-1" placeholder="جستجو" v-model="searchQuery" />
        <UButton @click="handleSearch" icon="i-lucide-search" variant="outline">بگرد</UButton>
      </UFieldGroup>
      <div id="items" class="flex-1 overflow-x-auto">
        <div v-if="fetchedItems.length != 0">
          <div v-for="item in fetchedItems" class="flex flex-col mb-2">
            <div class="size-full flex justify-start items-center p-2">
              <span>{{ item.name }}</span>
            </div>
          </div>
        </div>
        <div class="flex h-full justify-center items-center" v-else>
          <span>موردی برای نمایش وجود ندارد</span>
        </div>

      </div>
    </div>
    <!-- <UForm :state="state" class="space-y-4"> -->
    <!--   <UFormField label="Email" name="email" required> -->
    <!--     <UInput v-model="state.email" placeholder="shadcn@example.com" required /> -->
    <!--   </UFormField> -->
    <!--   <UFormField label="Password" name="password" required> -->
    <!--     <UInput v-model="state.password" placeholder="پسورد" required :type="showPassword ? 'text' : 'password'"> -->
    <!--       <template #trailing> -->
    <!--         <UButton color="neutral" variant="link" size="sm" :icon="showPassword ? 'i-lucide-eye-off' : 'i-lucide-eye'" -->
    <!--           :aria-label="showPassword ? 'Hide password' : 'Show password'" :aria-pressed="showPassword" -->
    <!--           aria-controls="password" @click="showPassword = !showPassword" /> -->
    <!--       </template> -->
    <!--     </UInput> -->
    <!---->
    <!--   </UFormField> -->
    <!---->
    <!--   <UButton label="Save changes" type="submit" /> -->
    <!-- </UForm> -->
  </DefineFormTemplate>

  <UModal v-if="isDesktop" v-model:open="open" :title="title">
    <UButton icon="i-lucide-search" variant="link" color="#fff" />

    <template #body>
      <ReuseFormTemplate />
    </template>
  </UModal>

  <UDrawer v-else v-model:open="open" :title="title">
    <UButton icon="i-lucide-search" variant="link" color="#fff" />

    <template #body>
      <ReuseFormTemplate />
    </template>
  </UDrawer>

</template>
