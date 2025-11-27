<script setup lang="ts">
import type { AuthFormField, FormSubmitEvent } from "@nuxt/ui";
import * as z from "zod";

const toast = useToast();

const fields: AuthFormField[] = [
  {
    name: 'email',
    type: 'email',
    label: 'ایمیل',
    placeholder: 'ایمیل خود را وارد کنید',
    required: true,
  },
  {
    name: 'password',
    type: 'password',
    label: 'رمزعبور',
    placeholder: 'رمزعبور خود را وارد کنید',
    required: true,
  },
];

const providers = [
  {
    icon: "i-simple-icons-google",
    onClick: () => {
      toast.add({ title: "Google", description: "Login With Google" })
    },
  }
];

const schema = z.object({
  email: z.email('Invalid Email'),
  password: z.string('Password is required').min(8, 'Must be at least 8 chars')
});

type Schema = z.output<typeof schema>


function onSubmit(payload: FormSubmitEvent<Schema>) {
  console.log('Submitted', payload)
}

</script>

<template>
  <div>
    <div class="flex flex-col items-center justify-center gap-4 p-4">
      <UPageCard>
        <UAuthForm :schema="schema" :fields="fields" :providers="providers" @submit="onSubmit" />
      </UPageCard>
    </div>
  </div>
</template>
