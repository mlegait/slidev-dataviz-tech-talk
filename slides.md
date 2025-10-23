---
theme: default
title: Slidev
info: |
  ## Slidev presentation
  What is it and why use it

  Learn more at [Sli.dev](https://sli.dev)
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
---

# We do talks about code

---

<div class="w-full h-full flex items-center justify-center">
  <div class="relative flex flex-col items-center -mt-[50px]">
    <div class="relative w-80 h-80">
      <img
        v-motion
        :initial="{ x: 800, y: -100, scale: 1.5, rotate: -50 }"
        :enter="final"
        class="absolute inset-0"
        src="https://sli.dev/logo-square.png"
        alt=""
      />
      <img
        v-motion
        :initial="{ y: 500, x: -200, scale: 2 }"
        :enter="final"
        class="absolute inset-0"
        src="https://sli.dev/logo-circle.png"
        alt=""
      />
      <img
        v-motion
        :initial="{ x: 600, y: 400, scale: 2, rotate: 100 }"
        :enter="final"
        class="absolute inset-0"
        src="https://sli.dev/logo-triangle.png"
        alt=""
      />
    </div>
    <div
      class="text-9xl text-[#2B90B6] -mt-[50px]"
      v-motion
      :initial="{ x: -160, opacity: 0 }"
      :enter="{ x: 0, opacity: 1, transition: { delay: 2000, duration: 1000 } }">
      Slidev
    </div>
  </div>
</div>

<!-- vue script setup scripts can be directly used in markdown, and will only affects current page -->
<script setup lang="ts">
const final = {
  x: 0,
  y: 0,
  rotate: 0,
  scale: 1,
  transition: {
    type: 'spring',
    damping: 10,
    stiffness: 20,
    mass: 2
  }
}
</script>

---

::code-group

```sh [yarn]
yarn create slidev
```

```sh [pnpm]
pnpm create slidev
```

```sh [npm]
npm init slidev@latest
```

::

<div v-click class="flex" mt-20px>
  <div class="flex items-center justify-items-center w-1/2">
    <img src="./assets/markdown-mark.svg" alt="Markdown" class="mx-auto" >
  </div>
  <div class="w-1/2">

::code-block

```md [slides.md]
---
theme: default // TODO change
title: Slidev
info: |
  ## Slidev presentation
  What is it and why use it

  Learn more at [Sli.dev](https://sli.dev)
mdc: true
---

# We do talks about code

---

The rest of the slides ...

---
```

::

  </div>
</div>

---

# Syntax coloring

<div grid grid-cols-2 gap-6>
<div flex flex-col gap-4>

```ts [greet.ts]
// Say Hello to the user
const greet = (name: string): string => {
  const message = `Hello, ${name}!`;
  return message.toUpperCase();
};
```

```py [greet.py]
# Say Hello to the user
def greet(name: str) -> str:
  message = f"Hello, {name}!"
  return message.upper()
```

</div>
<div flex flex-col gap-4>

```tsx [react]
// Title saying Hello to the user
export const Greet = ({ name }: { name: string }) => {
  const message = `Hello, ${name}!`;
  return (
    <Title className="greet__title" level={1}>
      {message.toUpperCase()}
    </Title>
  );
};
```

```css [styles.css]
/* Title saying Hello to the user */
.greet__title {
  color: #4f46e5;
  font-size: 1rem;
  font-weight: bold;
}
```

</div>
</div>

---

# Line Numbers and Line Highlighting

```ts {all|2,14|15|16-17|18}{lines:true,startLine:2}
import { match, P } from 'ts-pattern';

type Data =
  | { type: 'text'; content: string }
  | { type: 'img'; src: string };

type Result =
  | { type: 'ok'; data: Data }
  | { type: 'error'; error: Error };

const result: Result = ...;

const html = match(result)
  .with({ type: 'error' }, () => <p>Oups! An error occured</p>)
  .with({ type: 'ok', data: { type: 'text' } }, (res) => <p>{res.data.content}</p>)
  .with({ type: 'ok', data: { type: 'img', src: P.select() } }, (src) => <img src={src} />)
  .exhaustive();
```

https://sli.dev/features/code-block-line-numbers.html  
https://sli.dev/features/line-highlighting

---

# Shiki Magic Move

````md magic-move
```ts
const nextState = {
  ...baseState,
  player: {
    ...baseState.player,
    inventory: [
      ...baseState.player.inventory,
      {
        id: 3,
        name: "Phoenix Feather",
        rarity: "legendary",
      },
    ],
  },
};
```

```ts
import { produce } from "immer";

const nextState = produce(baseState, (draft) => {
  draft.player.inventory = [
    ...draft.player.inventory,
    {
      id: 3,
      name: "Phoenix Feather",
      rarity: "legendary",
    },
  ];
});
```

```ts
import { produce } from "immer";

const nextState = produce(baseState, (draft) => {
  draft.player.inventory.push({
    id: 3,
    name: "Phoenix Feather",
    rarity: "legendary",
  });
});
```
````

https://sli.dev/features/shiki-magic-move

---

# Monaco Editor

```ts {monaco}
import { produce } from "immer";
import { gameState } from "./state";

const newState = produce(gameState, (draft) => {
  const potion = draft.player.inventory.find((i) => i.name === "Health Potion");
  if (potion) {
    potion.quantity -= 1;
  }
  draft.player.stats.equipment.armor.head = "Steel Helmet";
  draft.player.inventory = draft.player.inventory.filter(
    (i) => i.name !== "Old Boots",
  );
  draft.player.inventory.push({
    id: 3,
    name: "Phoenix Feather",
    rarity: "legendary",
    quantity: 1,
  });
  draft.player.stats.mana += 10;
});
```

https://sli.dev/features/monaco-editor.html  
https://microsoft.github.io/monaco-editor/

---

# Monaco Runner

```ts {monaco-run}{ editorOptions: { lineNumbers:'on'} }
import { Temporal } from "temporal-polyfill";

const jsSophia11 = Temporal.ZonedDateTime.from(
  "2022-10-11T18:30:00[Europe/Paris]",
);
const jsSophia12 = Temporal.ZonedDateTime.from(
  "2023-06-15T18:17:43[Europe/Paris]",
);
const jsSophia13 = Temporal.ZonedDateTime.from(
  "2025-04-22T18:30:00[Europe/Paris]",
);

const jsSophia14 = jsSophia13.add(Temporal.Duration.from({ months: 2 }));
//console.log(jsSophia14);

//console.log(jsSophia13.since(jsSophia12)/*.toLocaleString()*/);
//console.log(jsSophia13.since(jsSophia12).round({smallestUnit: 'second'}).toLocaleString());
```

---
layout: iframe-unscaled-right

# the web page source
url: /components/parent-selector.html
---

# Writable Monaco Editor

<div flex flex-col gap-4>

```html
<form class="form">
  <label>
    Name
    <input type="text" />
  </label>
</form>
```

<<< ./components/parent-selector.css {monaco-write}{height:'120px'}

</div>

<!--
.form:has(input:focus) {
-->
