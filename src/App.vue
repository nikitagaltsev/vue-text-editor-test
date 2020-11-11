<template>
  <div id="app">
    <header class="header"><h1>Text editor on Vue.js</h1></header>
    <hr />
    <main>
      <Selectors :formatting="formatting" />

      <ContentEditable v-on:input="textEl = $event">
        {{ textEl }}
      </ContentEditable>

      <button class="JSON-btn" type="button" @click="convertToJSON">
        Make JSON great again
      </button>
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
      const span = document.createElement("span");

      span.style[parameter] = value;

      span.appendChild(range.extractContents());
      range.insertNode(span);
    },

    convertToJSON() {
      // создаём массив на основе children, благодаря return перезаписываем undefined на нужные свойства
      console.log(this.textEl.children);
      const arr = [...new Array(this.textEl.children.length)].map((el, idx) => {
        if (this.textEl.children[idx].style) {
          return {
            text: this.textEl.children[idx].textContent,
            fontSize: this.textEl.children[idx].style.fontSize,
            color: this.textEl.children[idx].style.color,
          };
        } else {
          return {
            text: this.textEl.textContent,
            fontSize: "30px",
            color: "black",
          };
        }
      });

      const finalArr = [];


      //проверка на похожие свойства в соседних объектах 
      arr.forEach((el) =>
        el.color === finalArr[finalArr.length - 1]?.color ??
        el.fontSize === finalArr[finalArr.length - 1]?.fontSize
          ? (finalArr[finalArr.length - 1].text += el.text)
          : finalArr.push(el)
      );

      console.log(JSON.stringify(finalArr));
    },
  },
};
</script>

<style>
#app {
  font-family: "Roboto", sans-serif;
}

.JSON-btn {
  display: block;
  margin: 20px auto;
}

.header,
.footer {
  text-align: center;
}
</style>
