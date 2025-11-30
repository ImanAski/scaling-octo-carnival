<script setup lang="ts">

import { createReusableTemplate, useMediaQuery } from '@vueuse/core';

const [DefineFormTemplate, ReuseFormTemplate] = createReusableTemplate();

const isDesktop = useMediaQuery('(min-width: 768px)');

const open = ref<boolean>(false);
const showPassword = ref<boolean>(false);

const state = reactive({
  email: undefined,
  password: undefined
})

const title = "ورود/ثبت نام";
</script>

<template>
  <DefineFormTemplate>
    <UForm :state="state" class="space-y-4">
      <UFormField label="Email" name="email" required>
        <UInput v-model="state.email" placeholder="shadcn@example.com" required />
      </UFormField>
      <UFormField label="Password" name="password" required>
        <UInput v-model="state.password" placeholder="پسورد" required :type="showPassword ? 'text' : 'password'">
          <template #trailing>
            <UButton color="neutral" variant="link" size="sm" :icon="showPassword ? 'i-lucide-eye-off' : 'i-lucide-eye'"
              :aria-label="showPassword ? 'Hide password' : 'Show password'" :aria-pressed="showPassword"
              aria-controls="password" @click="showPassword = !showPassword" />
          </template>
        </UInput>

      </UFormField>

      <UButton label="Save changes" type="submit" />
    </UForm>
  </DefineFormTemplate>

  <UModal v-if="isDesktop" v-model:open="open" :title="title">
    <UButton icon="i-lucide-user">
      ورود
    </UButton>

    <template #body>
      <ReuseFormTemplate />
    </template>
  </UModal>

  <UDrawer v-else v-model:open="open" :title="title">
    <UButton icon="i-lucide-user">
      ورود
    </UButton>

    <template #body>
      <ReuseFormTemplate />
    </template>
  </UDrawer>

</template>
