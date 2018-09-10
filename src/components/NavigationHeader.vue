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
    <div class="mushroom">
      <img src="../assets/mushroom.png" alt="mushroom">
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
    .mushroom {
      position: absolute;
      right: $lateral-padding-mobile;
      width: 35px;
      animation-name: mushroom-anim;
      animation-duration: 2s;
      animation-iteration-count: infinite;
      transition: transform 0.2s cubic-bezier(0, 0, 0.51, 1.29);
      img {
        width: 100%;
      }
    }
  }

  @keyframes mushroom-anim {
    0% { transform: scale(1) }
    50% { transform: scale(1.1) }
    100% { transform: scale(1) }
  }

</style>
