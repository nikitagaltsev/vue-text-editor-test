<template>
  <div class="select-container">
    <label for="color">Font Color: </label>
    <input
      class="color-input"
      type="color"
      name="color"
      @change="formatting('color', selectedColor)"
      v-model="selectedColor"
    />

    <label for="bgcolor">Background color: </label>
    <input
      class="color-input"
      type="color"
      name="bgcolor"
      @change="formatting('backgroundColor', selectedBG)"
      v-model="selectedBG"
    />

    <select
      class="select"
      v-model="selectedFontSize"
      @change="formatting('fontSize', selectedFontSize)"
    >
      <option value="" disabled class="select__option select__option_heading"
        >Font Size</option
      >
      <option value="14px" class="select__option">Small</option>
      <option value="30px" class="select__option">Medium</option>
      <option value="40px" class="select__option">Large</option>
    </select>
  </div>
</template>

<script>
export default {
  props: ["formatting"],
  data() {
    return {
      selectedFontSize: "",
      selectedColor: "",
      selectedBG: "",
    };
  },
};
</script>

<style scoped>
.select-container {
  text-align: center;
  margin: 20px auto;
  max-width: 450px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.select {
  margin: 10px;
}

.color-input {
  width: 50px;
  height: 20px;
}
</style>
