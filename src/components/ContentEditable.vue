<template>
  <div
    class="textarea"
    contenteditable="true"
    spellcheck="false"
    @input="getText"
  >
    <!-- <span
      style="background-color: rgb(248, 187, 208); padding-left:3px; padding-right: 3px; border-radius: 4px; font-size: 14px; color: white"
      >Hi</span
    >
    <span
      style="background-color: rgb(248, 187, 208); padding-left:3px; padding-right: 3px; border-radius: 4px; font-size: 14px; color: white"
      >My lovely</span
    >
    <span style="color: rgb(136, 14, 79); font-size: 54px">little</span>
    <span style="color: rgb(186, 104, 200); background-color: rgb(248, 187, 0);">
      Ponny
    </span> -->
  </div>
</template>

<script>
export default {
  methods: {
    getText() {
      //поднимаем div при инпуте 
      this.$emit("input", this.$el);
    },
  },
};
</script>

<style>
.textarea {
  padding: 10px;
  margin: 0 auto;
  width: 800px;
  height: 400px;
  align-self: center;
  border: 1px solid gray;
  border-radius: 10px;
  font-size: 30px;
}

div,
span {
  font-size: 22px;
  color: black;
  background-color: transparent;
}
</style>
