<template lang="html">

  <section class="rss-footer">
    <div class="item facebook">
      <a href="https://www.facebook.com/lazystacy/?ref=br_rs">
        <img src="../assets/Facebook.png" />
      </a>
    </div>
    <div class="item instagram">
      <a href="https://www.instagram.com/lazystacyband/?hl=eshttps://www.instagram.com/lazystacyband/?hl=es">
        <img src="../assets/Instagram.png" />
      </a>
    </div>
    <div class="item youtube">
      <a href="https://www.youtube.com/channel/UCbQ0O0kAUjdE65SRAQykayg">
        <img src="../assets/Youtube.png" />
      </a>
    </div>
  </section>

</template>

<script lang="js">
export default {
  name: 'rss-footer',
  props: [],
  mounted() {},
  data() {
    return {};
  },
  methods: {},
  computed: {}
};
</script>

<style scoped lang="scss">
  .rss-footer {
    position: fixed;
    z-index: 0;
    height: 95px;
    bottom: 0px;
    left: 0;
    background: rgba(0,0,0,0.5);
    display: flex;
    width: 100vw;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 0;
    .item {
      cursor: pointer;
      padding: 0 2rem;
      img {
        width: 100%;
      }
      animation-name: rss-anim;
      animation-duration: 3s;
      animation-iteration-count: infinite;
      transition: transform 0.2s cubic-bezier(0, 0, 0.51, 1.29);
      &.facebook {
        animation-delay: 1s;
      }
      &.instagram {
        animation-delay: 2s;
      }
      &.youtube {
        animation-delay: 3s;
      }
    }
  }
  @keyframes rss-anim {
    0% { opacity: 1 }
    50% { opacity: 0.8 }
    100% { opacity: 1 }
  }
</style>
