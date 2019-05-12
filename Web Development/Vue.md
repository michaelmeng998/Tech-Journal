# Notes from Learning Vue.js
Condensed version of notes from https://vuex.vuejs.org/guide

## Core Concepts from Learning Vuex
- Vuex uses a **single state tree** which means that this single object will contain all of an application's state level - means we only have a singular store

### Getting Vuex State into Vue Components
- Use the **computed** property to return some store state as below
- Whenever store.state.count changes, the computed property will be re-evaluated


```
const Counter = {
  template: `<div>{{ count }}</div>`,
  computed: {
    count () {
      return store.state.count
    }
  }
}
```

### How to inject store into all child components from root component
- Access in child components by using `this.$store`
```
const Counter = {
  template: `<div>{{ count }}</div>`,
  computed: {
    count () {
      return store.state.count
    }
  }
}
```

### The `mapState` Helper
- Use this when you have to make use of multiple store state properties or getters

```
import { mapState } from 'vuex'

export default {
  // ...
  computed: mapState({
    // arrow functions can make the code very succinct!
    count: state => state.count,

    // passing the string value 'count' is same as `state => state.count`
    countAlias: 'count',

    // to access local state with `this`, a normal function must be used
    countPlusLocalState (state) {
      return state.count + this.localCount
    }
  })
}
```

### Getters
 - This allows us to define computed properties for stores, which are only re-evaluated when dependencies have changed
 - Getters receive the state as the first argument as below
 ```
 const store = new Vuex.Store({
  state: {
    todos: [
      { id: 1, text: '...', done: true },
      { id: 2, text: '...', done: false }
    ]
  },
  getters: {
    doneTodos: state => {
      return state.todos.filter(todo => todo.done)
    }
  }
})
```
### Property-Style Access
- Getter are exposed to the `store.getters` object and you can access values as properties

`
store.getters.doneTodos // -> [{ id: 1, text: '...', done: true }] `

### Method-Style Access
- Can also pass arguments to getters by returning a function, useful for **querying an array in the store**

```
getters: {
  // ...
  getTodoById: (state) => (id) => {
    return state.todos.find(todo => todo.id === id)
  }
}


store.getters.getTodoById(2) // -> { id: 2, text: '...', done: false }
```

* Getters that are accessed via methods will run each time they're called, with the result not being cached

### Using `mapGetters` Helper
- Again this just maps store getters to local computed properties
- Just saves some time

```
import { mapGetters } from 'vuex'

export default {
  // ...
  computed: {
    // mix the getters into computed with object spread operator
    ...mapGetters([
      'doneTodosCount',
      'anotherGetter',
      // ...
    ])
  }
}
```

### Mutations:

- **ONLY WAY TO CHANGE STATE IN VUEX STORE**
- But **mutations are synchronous transactions**, must use actions to handle asynchronous operations
- Each ne has a string *type* and a *handler*

```
const store = new Vuex.Store({
  state: {
    count: 1
  },
  mutations: {
    increment (state) {
      // mutate state
      state.count++
    }
  }
})
```

- Can't directly call a mutation handler however. One must use `store.commit` with its type to invoke the mutation handler.


`store.commit('increment')`

### How are Actions Different?
Actions are similar but they just:
* They don't mutate state, actions commit mutations.
* Actions can contain arbitrary asynchronous operations




