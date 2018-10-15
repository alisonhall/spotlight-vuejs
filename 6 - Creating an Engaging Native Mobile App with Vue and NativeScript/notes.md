# Create an Engaging Native Mobile App with Vue and NativeScript

with Jen Looper

@jenlooper

---

Nativescript is a framework for building native cross-platform mobile apps.

Use JavaScript, CSS, XML to build NativeScript. Can use no framework, Vue.js, Angular, etc.

NativeScript-Vue.org

Vue 2.0 adopts the virtual DOM, which enabled native mobile rendering.

Vue is lightweight.

Web: `import Vue from 'vue';`

NativeScript: `import Vue from 'nativescript-vue';`

When developing for NativeScript instead of the web, you don't reference the 'el' element when creating a Vue element, due to NativeScript not having a DOM to manipulate.

When developing for NativeScript instead of the web, the templating is slightly different

Playground:
play.nativescript.org

```
tns create MyApp
cd myApp
npm install --save nativescript-vue
```

Vue-CLI template
```
npm install -g @vue/cli @vue/cli-init
vue init nativescript-vue/vue-cli-template <project-name>
cd <project-name>
npm install
npm run watch:<platform>
```

---

https://github.com/nativescript-vue/nativescript-vue

NativeScript Slack

Plugins: market.nativescript.org
