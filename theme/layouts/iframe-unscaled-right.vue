<script setup lang="ts">
const props = defineProps<{
  url: string;
}>();

const unscaledSize = "calc(100% * var(--slidev-slide-scale))";
const unscaledTransform = "scale(calc(1 / var(--slidev-slide-scale)))";
</script>

<template>
  <div class="slidev-layout iframe-unscaled-right h-full w-full flex">
    <!-- Left column: custom content -->
    <div class="flex-1 overflow-auto">
      <slot />
    </div>

    <!-- Right column: unscaled iframe -->
    <div class="h-full overflow-auto min-h-0 flex-none" style="width: 50%">
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
