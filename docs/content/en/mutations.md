---
title: Mutations
description: 'Vanilla, strongly-typed store accessor.'
category: Store
position: 22
---

Mutations are functions that receive store state and an optional payload.

This package provides a helper function to reduce boilerplate: `mutationTree`. This function adds typings and returns the mutations passed to it, without transforming them.

```ts
// Vanilla

export const mutations = {
  setEmail(state: RootState, newValue: string) {
    state.email = newValue
  },

  initialiseStore() {
    console.log('initialised')
  },
}

// Helper function

import { mutationTree } from 'typed-vuex'

export const mutations = mutationTree(state, {
  setEmail(state, newValue: string) {
    state.email = newValue
  },

  initialiseStore() {
    console.log('initialised')
  },
})
```

<d-alert type="info">

1. Even if you do not use the `mutationTree` helper function, make sure not to use the `MutationTree` type provided by Vuex. This will interfere with type inference. You won't lose out by omitting it, as Typescript will complain if you pass an improperly formed mutation into [the `getAccessorType` function](/getting-started-nuxt#add-type-definitions).

2. This package does not support [object-style commits](https://vuex.vuejs.org/guide/mutations.html#object-style-commit).

</d-alert>
