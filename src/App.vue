<template>
  <div id="app">
    <Header></Header>
    <Editor />
  </div>
</template>

<script>
import Editor from "./components/Editor.vue";
import Header from "./components/Header.vue";

export default {
  name: "App",
  components: {
    Editor,
    Header
  }
};
</script>

<style lang="scss">
@import "~bootstrap/scss/functions";
@import "~bootstrap/scss/variables";
@import "~bootstrap/scss/mixins";
@import "~bootstrap/scss/dropdown";
@import "~bootstrap/scss/grid";
@import "~bootstrap/scss/utilities";
@import "~bootstrap/scss/reboot";
@import "../node_modules/@braid/vue-formulate/themes/snow/snow.scss";

.formulate-input {
  .formulate-input-label {
    font-size: 0.6em;
    margin-bottom: 0;
  }
}

ul.formulate-input-errors {
  font-size: 0.6em;
  line-height: 1;

  .formulate-input-error {
    font-size: inherit;
  }
}

.formulate-input .formulate-input-element {
  max-width: none;
}

.line-nowrap.formulate-input {
  label {
    white-space: nowrap;
  }
}

#app {
  font-family: Segoe UI, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  background: rgba(65, 184, 130, 1);
  background: linear-gradient(
    45deg,
    rgba(65, 184, 130, 1) 0%,
    rgba(242, 246, 250, 1) 100%
  );
  filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#41b882', endColorstr='#f2f6fa', GradientType=1 );
  min-height: 100vh;
}
</style>
