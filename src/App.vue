<template>
  <div>
    <header class="header"><h1>Text editor on Vue.js</h1></header>
    <hr />
    <main>
      <div class="select-container">
        <select class="select" v-model="selectedFont" @change="formatFontSize">
          <option
            value=""
            disabled
            class="select__option select__option_heading"
            >Font Size</option
          >
          <option value="small" class="select__option">Small</option>
          <option value="medium" class="select__option">Medium</option>
          <option value="large" class="select__option">Large</option>
        </select>

        <select class="select" v-model="selectedColor" @change="formatColor">
          <option
            value=""
            class="select__option select__option_heading"
            disabled
            >Text Color</option
          >
          <option value="red" class="select__option">Red</option>
          <option value="green" class="select__option">Green</option>
          <option value="blue" class="select__option">Blue</option>
          <option value="black" class="select__option">Black</option>
        </select>

        <select class="select" v-model="selectedBG">
          <option
            value=""
            class="select__option select__option_heading"
            disabled
            >Background</option
          >
          <option value="red" class="select__option">Red</option>
          <option value="green" class="select__option">Green</option>
          <option value="blue" class="select__option">Blue</option>
          <option value="black" class="select__option">Black</option>
        </select>
      </div>

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
import ContentEditable from "./components/ContentEditable";
export default {
  components: {
    ContentEditable,
  },
  data() {
    return {
      selectedFont: "",
      selectedColor: "",
      selectedBG: "",
      selectedRange: null,
      textEl: "",
    };
  },
  methods: {
    getYear() {
      return new Date().getFullYear();
    },
    formatFontSize() {
      console.log(this.selectedFont);
    },
    formatColor() {
      const sel = window.getSelection();
      console.log(this.textEl);
      console.dir(sel)
      console.log(sel.anchorOffset, sel.focusOffset);
      const span = `<span style="color: ${this.selectedColor}">${this.textEl.innerHTML
        .split("")
        .slice(sel.anchorOffset, sel.focusOffset)
        .join("")}</span>`;

      const before = this.textEl.innerHTML
        .split("")
        .slice(0, sel.anchorOffset)
        .join("");

      const after = this.textEl.innerHTML
        .split("")
        .slice(sel.focusOffset)
        .join("");

      console.log(before, after);
      console.log(span);

      this.textEl.innerHTML = ''
      this.textEl.innerHTML = before + span + after;

      console.log(this.textEl);
    },
  },
};
</script>

<style scoped>
.header {
  text-align: center;
}

.footer {
  text-align: center;
}

.select-container {
  text-align: center;
  margin: 20px auto;
  max-width: 600px;
}

.select {
  margin: 10px;
}
</style>
