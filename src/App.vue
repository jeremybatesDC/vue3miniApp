<template>
  <!-- in vue3, even though 1 root node still seems like a good practice, now you may have multiple root nodes-->
  <header class="header--global">
    <h1>BrewPub Finder</h1>
    <label class="label--darkMode">
      <input type="checkbox" :value="isDarkMode" @change="toggleDarkMode">
      <span> Dark Mode</span>
    </label>
  </header>
  <main :class="['wrapper--outer', { darkMode: isDarkMode }]">
    <BreweryList />
  </main>
</template>

<script>
import BreweryList from "./components/BreweryList.vue";

export default {
  name: "App",
  components: {
    BreweryList,
  },
  computed: {
    isDarkMode() {
      return this.$store.state.isDarkMode;
    },
  },
  methods: {
    toggleDarkMode() {
      this.$store.commit("toggleDarkMode");
    },
  },
};
</script>

<style>

/*CSS Reset per Josh Comeau*/

*, *::before, *::after {
  box-sizing: border-box;
}
* {
  margin: 0;
}
html, body {
  height: 100%;
}
body {
  line-height: 1.5;
  -webkit-font-smoothing: antialiased;
}

img, picture, video, canvas, svg {
  display: block;
  max-width: 100%;
}

img {
  height: auto;
}

input, button, textarea, select {
  font: inherit;
}
p, h1, h2, h3, h4, h5, h6 {
  overflow-wrap: break-word;
}
#root, #__next {
  isolation: isolate;
}

h1, h2, h3, h4, h5, h6 {
  line-height: 1.1111;
}
/* end CSS reset */
h1 {
  font-size: 1.5rem;
}

ul {
  list-style: none;
  padding: 0;
}

label span,
label div {
  user-select: none;
  -webkit-tap-highlight-color: transparent;
  white-space: nowrap;
}

#app {
  font-family: -apple-system, BlinkMacSystemFont, avenir next, avenir, segoe ui, helvetica neue, helvetica, Ubuntu, roboto, noto, arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #000;
	background: #fff;

}

[v-cloak] {
  display: none;
}

.darkMode *:not(img, figure) {
	filter: invert(100%);
}

.header--global {
  position: sticky;
  top: 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.5rem 1rem;
  min-height: var(--headerHeight);
  background: #000;
  color: #fff;
  border-bottom: 1px solid #fff;
}

.label--darkMode {
  white-space: nowrap;
}

</style>
