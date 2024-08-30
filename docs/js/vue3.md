# Vue 3 Composition API avec `script setup` Cheat Sheet

## Introduction

Vue 3 introduit la Composition API, une nouvelle façon d'organiser et de structurer les composants. La Composition API permet de mieux réutiliser la logique et offre plus de flexibilité par rapport à l'API Options classique.

## Syntaxe de Base

### Composant Simple avec `script setup`

```vue
<template>
  <div>{{ message }}</div>
</template>

<script setup>
import { ref } from "vue";

const message = ref("Hello, Vue 3!");
</script>
```

### Variables Réactives

- Utiliser `ref` pour créer une valeur réactive simple.

```javascript
import { ref } from "vue";

const count = ref(0);
```

- Utiliser `reactive` pour créer un objet réactif.

```javascript
import { reactive } from "vue";

const state = reactive({
  count: 0,
  name: "Vincent",
});
```

### Exposer des Variables à Template

Toutes les variables définies dans le bloc `script setup` sont automatiquement exposées au template.

```vue
<template>
  <div>{{ count }}</div>
</template>

<script setup>
import { ref } from "vue";

const count = ref(0);
</script>
```

### Méthodes et Fonctions

- Définir des fonctions directement dans le bloc `script setup`.

```vue
<template>
  <button @click="increment">Increment</button>
</template>

<script setup>
import { ref } from "vue";

const count = ref(0);

function increment() {
  count.value++;
}
</script>
```

### Props

- Utiliser la directive `defineProps` pour déclarer des props.

```vue
<template>
  <div>{{ msg }}</div>
</template>

<script setup>
const props = defineProps({
  msg: String,
});
</script>
```

### Événements

- Utiliser `emit` pour émettre des événements.

```vue
<template>
  <button @click="emitEvent">Click Me</button>
</template>

<script setup>
const emit = defineEmits(["myEvent"]);

function emitEvent() {
  emit("myEvent", "Hello World");
}
</script>
```

### Lifecycle Hooks

Les hooks de cycle de vie peuvent être utilisés directement dans le bloc `script setup`.

```javascript
import { onMounted, onUnmounted } from "vue";

onMounted(() => {
  console.log("Component mounted");
});

onUnmounted(() => {
  console.log("Component unmounted");
});
```

## Utilisation des Composants

- Importer un composant enfant dans un composant parent avec `script setup`.

```vue
<template>
  <ChildComponent />
</template>

<script setup>
import ChildComponent from "./ChildComponent.vue";
</script>
```

## Requêtes API

- Utiliser `axios` ou `fetch` pour les requêtes API.

```vue
<template>
  <div v-if="data">{{ data }}</div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import axios from "axios";

const data = ref(null);

onMounted(async () => {
  const response = await axios.get("https://api.example.com/data");
  data.value = response.data;
});
</script>
```

## Exemples Avancés

### Usage de `computed`

```vue
<template>
  <div>{{ doubled }}</div>
</template>

<script setup>
import { ref, computed } from "vue";

const count = ref(2);
const doubled = computed(() => count.value * 2);
</script>
```

### Formulaires Réactifs

```vue
<template>
  <form @submit.prevent="handleSubmit">
    <input v-model="form.name" placeholder="Name" />
    <button type="submit">Submit</button>
  </form>
</template>

<script setup>
import { reactive } from "vue";

const form = reactive({
  name: "",
});

function handleSubmit() {
  console.log(form.name);
}
</script>
```
