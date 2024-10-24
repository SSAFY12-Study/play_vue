<script setup>
import { RouterView } from 'vue-router'
import AppBarView from '@/components/AppBarView.vue'
</script>

<template>
  <header>
    <AppBarView></AppBarView>
  </header>
  <RouterView />
</template>

<style scoped></style>
