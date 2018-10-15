# The Importance of State Management in Vue

with Hassan Djirdeh

@djirdehh

---

## Simple Data passing

Use props to pass data from the parent to the child

Use vue-custom-events to pass data from the child to the parent

On child: `this.$emit('custom-event');`

On parent: catch the event from the child (... `.$on(...)` ...)

Can use an Event Bus to pass data between children or isolated components, but should ideally upgrade to using a store

```js
EventBus = new Vue();
```

```js
created() {
    EventBus.$on('event', (e) => {
        console.log('fired');
    });
}
```

---

## Complex Data passing = Stores

Store and store mutator:
```js
store = {
    state: (
        talk: 'skldfksdjf',
        speaker: 'slkdfjlsfj'
    ),
    changeSpeaker(newSpeaker) {
        this.state.speaker = newSpeaker
    }
}
```

Getter:
```js
componentA

data() {
    return {
        sharedState: store.state
    }
}
```

Action:
```js
componentB

methods: {
    changeSpeaker() {
        store.changeSpeaker('slkdfl');
    }
}
```

* Action
* Dispatcher
* Store
* View

`npm install ` vuex

`Vue.use(Vuex)`

```js
const store = new Vuex.Store({
    state,
    mutations,
    actions,
    getters
})

new Vue({
    el: '#app,
    store,
    render: ...
})
```

```js
const actions = {
    updateSpeaker(context) {
        axios.get('/api/speakers').then((response) => {
            context.commit('UPDATE_SPEAKER', response.speaker[0]);
        });
    }
}
```

```js
const getters = {
    getSpeaker(state) {
        return state.speaker;
    }
}
```


```
<template>
    <h1 @client="updateSpeaker">
        The speaker is {{getSpeaker}}
    </h1>
</template>

<script>
export default {
    name: 'SpeakerComponent',
    computed: {
        getSpeaker() {
            return this.$store.getters.getSpeaker;
        }
    }
},
methods: {
    updateSpeaker() {
        this.$store.dispatch('updateSpeaker');
    }
}
</script>
```

Simplify the previous example by using:
```js
import { mapGetters, mapActions } from 'vuex';
```

Vuex extends a simple store by introducing explicityly defined getters, mutations, and actions

Vuex integrates with the Vue devtools for time-travel debugging

Vuex modules can have their own states, actions, mutations, and getters.

Vuex stores follow the flux architecture

Vuex stores should be:

* Malleable

* Maintainable

* Manageable

---

Fullstack Vue book (to be released March 14th, 2018):

https://www.fullstack.io/vue