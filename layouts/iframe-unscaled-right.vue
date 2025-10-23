<script setup lang="ts">
const props = defineProps<{
  url: string;
}>();

const unscaledSize = "calc(100% * var(--slidev-slide-scale))";
const unscaledTransform = "scale(calc(1 / var(--slidev-slide-scale)))";
</script>

<template>
  <div class="h-full w-full flex gap-4 p-6">
    <!-- Left column: custom content -->
    <div class="flex-1 overflow-auto">
      <slot />
    </div>

    <!-- Right column: unscaled iframe -->
    <div class="flex-1 h-full overflow-auto min-h-0">
      <div
        :style="{
          width: unscaledSize,
          height: unscaledSize,
        }"
      >
        <iframe
          id="frame"
          class="w-full h-full"
          :src="url"
          :style="{ transform: unscaledTransform, transformOrigin: 'top left' }"
        />
      </div>
    </div>
  </div>
</template>

<style scoped></style>
