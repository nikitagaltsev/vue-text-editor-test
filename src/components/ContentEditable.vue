<template>
  <div
    class="textarea"
    contenteditable="true"
    spellcheck="false"
    @input="getText"
  >

  <span style="color: rgb(255, 0, 0);">Y</span><span style="color: rgb(255, 0, 0);">A<span style="font-size: 14px;"></span></span><span style="font-size: 14px;">ND</span>EX <span style="background-color: rgb(255, 0, 128);">prakt</span>ik<span style="color: rgb(0, 255, 255);">um</span> <span style="font-size: 40px;">4ever</span><br>


  </div>
</template>

<script>
export default {
  methods: {
    getText() {
      this.$emit('input', this.$el)
    }
  }
};
</script>

<style scoped>
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
</style>
