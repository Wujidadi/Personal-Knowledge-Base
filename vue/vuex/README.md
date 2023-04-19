# Vuex

## Vuex 4 大核心概念 (Core Concepts)

> 2023-02-10 16:39:  
> 才剛寫完這篇就發現 Vuex 5 被 Pinia 取代了😢😡

### 0. namespaced

While in a module

### 1. state

`mapState` to `computed`, but work like `data`

### 2. getters

Get `state`s; `mapGetters` to `computed`  
Parameters:  
`(1) state`  
`(2) getters`: access other getters  
`(3) rootState` and `(4) rootGetters` to access the `state`/`getters` of the root while it is in a module

### 3. mutation

**Sync**; should be called through `commit`; `mapMutations` to `methods`

### 4. action

**Async**; invoke `mutation`s through `commit`; should be called through `dispatch`; `mapActions` to `methods`  
The first param is an object, includes the 4 parts (called on demand):  
`(1) state`  
`(2) getters`  
`(3) commit`  
`(4) dispatch`

### Example

#### app.js

```javascript
import { createApp } from 'vue';
import { createRouter } from 'vue-router';
import { createStore } from 'vuex';

import moduleA from './moduleA';
const store = createStore({
    state() { return { ... }; },
    getters: { ... },
    mutations: { ... },
    actions: { ... },
    modules: {
        moduleA: moduleA,
    },
});

const router = createRouter({
    // history, routes, ...
});

createApp({
    // components, data, methods, ...
})
.use(store)
.use(router)
.mount('#app');
```

#### moduleA.js

```javascript
const storeModule = {
    namespaced: true,
    state() {
        return {
            theWorld: [
                'shijie',
                'za warudo',
            ],
        };
    },
    getters: {
        jojoWorld: (state, getters, rootState, rootGetters) => (index, follow = true) => {
            return follow ? state.theWorld[index] + '!' : 'ザ・ワールド！';
        },
    },
    mutations: {
        setNewWorld(state, newWorld) {
            state.theWorld.push(newWorld);
        },
    },
    actions: {
        createNewWorld({ commit }, newWorld) {
            commit('setNewWorld', newWorld);
        },
        async getNewWorld({ state, getters, commit, dispatch }) {
            await axios.get('/api/world')
            .then(response => {
                if (response.data.world !== getters.jojoWorld(response.data.index)) {
                    dispatch('createNewWorld', response.data.world);
                }
            })
            .catch(error => {
                console.warn(error);
            });
        },
    },
};

export default storeModule;
```

#### component.vue

```vue
<template>
    ...
</template>

<script>
    import { mapState, mapGetters, mapMutations, mapActions } from 'vuex';

    export default {
        components: { ... },
        data() { return { ... }; },
        computed: {
            ...mapState('moduleA', [
                theWorld: state => state.theWorld,
            ]),
            ...mapGetters('moduleA', [
                theWorld: 'theWorld',
            ]),
        },
        methods: {
            ...mapMutations('moduleA', [
                setNewWorld: 'setNewWorld',
            ]),
            ...mapActions('moduleA', [
                createNewWorld: 'createNewWorld',
                getNewWorld: 'getNewWorld',
            ]),
        },
    };
</script>

<style lang="scss" src="@/xxx.scss" scoped></style>
```
