<script setup>
import Button from '@/components/Button.vue'
</script>
<template>
  <div class="z-20 relative">
    <div class="bg-black/70 fixed top-0 left-0 h-dvh w-full grid place-items-center">
      <div class="p-4 bg-white flex flex-col gap-4 items-center w-full max-w-2xl min-h-60">
        <slot></slot>
        <Button @click="$emit('close-modal', false)">Close</Button>
      </div>
    </div>
  </div>
</template>
