<script>
import MainHeader from "./components/MainHeader.vue";
import MainBody from "./components/MainBody.vue";
import MainFooter from "./components/MainFooter.vue";

export default {
  components: { MainHeader, MainBody, MainFooter },
};
</script>

<template>
  <div>
    <main-header></main-header>
    <main-body></main-body>
    <main-footer></main-footer>
  </div>
</template>
