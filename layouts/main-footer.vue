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
  <div class="slidev-layout main-footer h-full w-full relative">
    <main>
      <slot />
    </main>
    <footer class="opacity-80 text-sm absolute left-15 right-10 top-112">
      <slot name="footer" />
    </footer>
  </div>
</template>

<style scoped></style>
