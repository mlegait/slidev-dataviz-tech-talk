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
    class="slidev-layout title-two-cols-footer h-full w-full grid grid-rows-[auto,1fr,auto] gap-2"
  >
    <header>
      <slot name="title" />
    </header>

    <main class="grid grid-cols-1 md:grid-cols-2 gap-6 min-h-0">
      <section class="min-h-0 overflow-auto">
        <slot name="left" />
      </section>
      <aside class="min-h-0 overflow-auto">
        <slot name="right" />
      </aside>
    </main>

    <footer class="mt-2 opacity-80 text-sm">
      <slot name="footer" />
    </footer>
  </div>
</template>

<style scoped></style>
