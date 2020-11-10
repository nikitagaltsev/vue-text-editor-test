<template>
  <div
    class="textarea"
    contenteditable="true"
    spellcheck="false"
    @input="getText"
  >
    
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
  height: 800px;
  align-self: center;
  border: 1px solid gray;
  border-radius: 10px;
  font-size: 30px;
}
</style>
