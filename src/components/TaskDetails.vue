<template>
  <div class="task">
    <h3>{{ task.title }}</h3>
    <div class="icons">
      <i class="material-icons">delete</i>
      <i class="material-icons" @click="$emit('favoriteTask')">favorite</i>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps(['task'])

const emit = defineEmits(['favoriteTask'])
</script>

<style lang="scss" scoped>
</style>
