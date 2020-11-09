<template>
  <div>
    <header class="header"><h1>Text editor on Vue.js</h1></header>
    <hr />
    <main>
      <textarea class="textarea">

      </textarea>
    </main>
    <footer class="footer">
      <p>
        {{ getYear() }} © Nikita Galtsev. Test task for Redentu.
      </p>
    </footer>
    </footer>
  </div>
</template>

<script>
export default {
  methods: {
    getYear() {
      return new Date().getFullYear();
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
</style>
