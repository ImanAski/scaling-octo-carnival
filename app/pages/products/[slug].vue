<script setup lang="ts">
const route = useRoute();
</script>

<template>
  <div>
    <h1>Product Page</h1>
    {{ route.params.slug }}
  </div>
</template>
