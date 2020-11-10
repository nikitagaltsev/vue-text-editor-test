<template>
  <div id="app">
    <header class="header"><h1>Text editor on Vue.js</h1></header>
    <hr />
    <main>
      <Selectors
        :formatting="formatting"
      />

      <ContentEditable v-on:input="textEl = $event">
        {{ textEl }}
      </ContentEditable>
    </main>
    <footer class="footer">
      <p>{{ getYear() }} © Nikita Galtsev. Test task for Redentu.</p>
    </footer>
  </div>
</template>

<script>
import Selectors from "./components/Selectors";
import ContentEditable from "./components/ContentEditable";
export default {
  components: {
    Selectors,
    ContentEditable,
  },
  data() {
    return {
      textEl: "",
    };
  },
  methods: {
    getYear() {
      return new Date().getFullYear();
    },
    formatting(parameter, value) {
      const range = window.getSelection().getRangeAt(0);
      const span = document.createElement('span');

      span.style[parameter] = value;

      span.appendChild(range.extractContents());
      range.insertNode(span);
    },
  },
};
</script>

<style scoped>
#app {
  font-family: "Roboto", sans-serif;
}

.header {
  text-align: center;
}

.footer {
  text-align: center;
}

</style>
