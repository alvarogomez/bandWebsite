<template lang="html">

  <section class="home">
    <navigation-header></navigation-header>
    <div class="heading">
      <h1>Lazy Stacy</h1>
      <span class="copy-small">Your next favourite Power-Trio</span>
      <p>
        Check out the band's website to discover info and listen and watch the groups multimedia.<br />
        Follow us in the RRSS to maintain you updated
      </p>
    </div>
    <div class="home-photo">
      <img src="../assets/psychedelic.jpg" alt="">
    </div>
    <div class="trio-container">
      <div class="item">
        <span class="component-name">Álvaro</span>
        <img src="../assets/guitaramp.png" />
      </div>
      <div class="item">
        <span class="component-name">Alberto</span>
        <img src="../assets/alberto.png" />
      </div>
      <div class="item">
        <span class="component-name">Jose</span>
        <img src="../assets/bassamp.png" />
      </div>
    </div>
    <rss-footer></rss-footer>
  </section>

</template>

<script lang="js">
import NavigationHeader from '../components/NavigationHeader';
import RssFooter from '../components/RssFooter';
export default {
  name: 'home',
  components: {
    NavigationHeader,
    RssFooter
  },
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
  @import '../variables';
  .home {
    padding: 0 $lateral-padding-mobile;
    min-height: 100vh;
    width: 100vw;
    position: relative;
    $homeShadow: 5px 1px 5px 1px rgba(0,0,0,0.2);
    .heading {
      display: flex;
      flex-direction: row;
      flex-wrap: wrap;
      justify-content: center;
      padding: 2rem $lateral-padding-mobile;
      // border-top: 2px dotted $main-text-color;
      // border-bottom: 2px dotted $main-text-color;
      margin-left: -$lateral-padding-mobile;
      margin-right: -$lateral-padding-mobile;
      box-shadow: 5px 1px 5px 1px rgba(0,0,0,0.2);
      h1 {
        font-size: 40px;
        width: 100%;
        margin-bottom: 1.5rem;
      }
      p {
        font-size: 16px;
        margin-top: 1rem;
      }
      .copy-small {
        font-size: 14px;
        display: block;
        font-style: italic;
      }
    }
    .home-photo {
      background-color: $background-nav-header;
      margin-left: -$lateral-padding-mobile;
      margin-right: -$lateral-padding-mobile;
      margin-top: 0;
      margin-bottom: 0;
      padding-top: 1rem;
      padding-bottom: 1rem;
      img {
        width: 100%;
        box-shadow: $homeShadow;
      }
    }
    .trio-container {
      background: rgba(0,0,0,0.05);
      padding-top: 1rem;
      padding-bottom: 1rem;
      margin: -$lateral-padding-mobile;
      margin-top: 0;
      margin-bottom: 0;
      box-shadow: $homeShadow;
      &:after {
        content: "";
        clear: both;
        display: table;
      }
      .item {
        width: 33.333%;
        float: left;
        padding: 0 2rem;
        &:first-child {
          text-align: left;
        }
        &:last-child{
          text-align: right;
        }
        .component-name {
          display: block;
          font-size: 12px;
          text-transform: uppercase;
          font-weight: 700;
          margin-bottom: 1rem;
        }
        img {
          width: 100%;
        }
      }
    }
  }
</style>
