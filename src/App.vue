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
      console.log(window.getSelection());

      span.appendChild(range.extractContents());
      range.insertNode(span);



      // document.querySelector(".textarea").insertBefore(span.appendChild(range.extractContents()), window.getSelection().focusNode.parentNode)


      // if (window.getSelection().focusNode.parentNode.tagName === 'SPAN') {
      //   console.log(1234);
      //   document
      //     .querySelector(".textarea")
      //     .insertBefore(
      //       span.appendChild(range.extractContents()),
      //       window.getSelection().anchorNode
      //     );
      // } else {
      //   span.appendChild(range.extractContents());
      //   range.insertNode(span);
      // }
    },

    convertToJSON() {
      const finalArr = []
      const markup = this.textEa;
      console.log(this.textEl.childNodes)

      // const finalArr = [...new Array(this.textEl.childNodes.length)].map((el, idx) => {
      //   for (let item of this.textEl.childNodes) {
      //     console.log();
      //   }
      // })

      // for (let item of this.textEl.childNodes) {
        
      // }

      for (let i = 0; i <= this.textEl.childNodes.length; i++) {
        console.log(this.textEl.childNodes[i])
      //   finalArr[i] = {
      //     fontSize: this.textEl.childNodes[i].style.fontSize
      //   }
      // }

      // console.log(finalArr);
    },
  },
};
</script>

<style scoped>
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
