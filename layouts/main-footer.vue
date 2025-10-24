<!--
  Usage:

```md
---
layout: main-footer
---

::footer::
Footer text or references.
```
-->

<script setup lang="ts"></script>

<template>
  <div
    class="slidev-layout main-footer h-full w-full grid grid-rows-[1fr,auto] gap-2 relative"
  >
    <main class="min-h-0 overflow-auto pb-12">
      <slot />
    </main>
    <footer class="opacity-80 text-sm absolute left-15 right-10 top-112">
      <slot name="footer" />
    </footer>
  </div>
</template>

<style scoped></style>
