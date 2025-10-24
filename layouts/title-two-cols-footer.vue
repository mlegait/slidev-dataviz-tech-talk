<!--
  Usage:

```md
---
layout: title-two-cols-footer
---

::title::
# My Title

::left::
- Point A
- Point B

::right::
Some content on the right.

::footer::
Footer text or references.
```
-->

<script setup lang="ts"></script>

<template>
  <div
    class="slidev-layout title-two-cols-footer h-full w-full flex flex-col gap-2"
  >
    <slot name="title" />

    <main class="flex gap-6">
      <section class="flex-1">
        <slot name="left" />
      </section>
      <section class="flex-1">
        <slot name="right" />
      </section>
    </main>

    <footer class="opacity-80 text-sm absolute left-15 right-10 top-112">
      <slot name="footer" />
    </footer>
  </div>
</template>

<style scoped></style>
