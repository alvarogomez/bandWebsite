<template lang="html">

  <section class="navigation-header">
    <div class="hamburger">
      <div id="nav-icon2">
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
      </div>
    </div>
  </section>

</template>

<script lang="js">
export default {
  name: 'navigation-header',
  props: ['iconType'],
  mounted() {},
  data() {
    return {};
  },
  methods: {},
  computed: {}
};
</script>

<style scoped lang="scss">
@import '../variables';
@import 'navIconAnimation';
  .navigation-header {
    position: relative;
    height: 60px;
    display: flex;
    align-items: center;
    background-color: $background-nav-header;
    margin-left: -$lateral-padding-mobile;
    margin-right: -$lateral-padding-mobile;
    margin-top: 0;
    .hamburger {
    }
  }

</style>
