<template lang="html">

  <section class="home">
    <navigation-header @mush="clickPsych"></navigation-header>
    <div class="heading">
      <h1 v-bind:class="{ psych: psychedelicMode }" >Lazy Stacy</h1>
      <span v-bind:class="{ psych: psychedelicMode }" class="copy-small">Your next favourite Power-Trio</span>
      <p v-bind:class="{ psych: psychedelicMode }">
        Check out the band's website to discover info and listen and watch the groups multimedia.<br />
        Follow us in the RRSS to maintain you updated
      </p>
    </div>
    <div class="home-photo">
      <img v-bind:class="{ psych: psychedelicMode }" src="../assets/psychedelic.jpg" alt="">
    </div>
    <div class="trio-container">
      <div class="item rotate-1" v-bind:class="{ psychrotate: psychedelicMode }">
        <span class="component-name">Álvaro</span>
        <img src="../assets/guitaramp.png" />
      </div>
      <div class="item rotate-2" v-bind:class="{ psychrotate: psychedelicMode }">
        <span class="component-name">Alberto</span>
        <img src="../assets/alberto.png" />
      </div>
      <div class="item rotate-3" v-bind:class="{ psychrotate: psychedelicMode }">
        <span class="component-name">Jose</span>
        <img src="../assets/bassamp.png" />
      </div>
    </div>
    <rss-footer v-bind:class="{ psychrotaterss: psychedelicMode }"></rss-footer>
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
  data() {
    return {
      psychedelicMode: false
    }
  },
  methods: {
    clickPsych() {
      this.$emit('home-on-psych');
    },
  },
  props: [],
  mounted() {
    this.$eventBus.$on('enter-psychedelic-mode', () => {
      this.psychedelicMode = true;
      var self = this;
      setTimeout(function(){
        self.psychedelicMode = false;
      }, 5000)
    });
  }
};
</script>

<style scoped lang="scss">
  @import '../variables';
  .home {
    .psychrotate {
      animation-name: roto-psych;
      animation-duration: 2.5s;
      animation-iteration-count: infinite;
      transition: transform 0.2s linear;
      &.rotate-1{
        animation-delay: 0s;
      }
      &.rotate-2{
        animation-delay: 0.25s;
      }
      &.rotate-3{
        animation-delay: 0.5s;
      }
    }
    .psychrotaterss {
      animation-name: roto-psych-rss;
      animation-duration: 5s;
      animation-iteration-count: infinite;
      transition: transform 0.2s linear;
    }
    padding: 0 $lateral-padding-mobile;
    min-height: 100vh;
    width: 100vw;
    position: relative;
    .heading {
      display: flex;
      flex-direction: row;
      flex-wrap: wrap;
      justify-content: center;
      padding: 2rem $lateral-padding-mobile;
      border-top: 2px dotted $main-text-color;
      border-bottom: 2px dotted $main-text-color;
      margin-left: -$lateral-padding-mobile;
      margin-right: -$lateral-padding-mobile;
      h1 {
        font-size: 40px;
        width: 100%;
        margin-bottom: 1.5rem;
        &.psych {
          animation-name: logo-psych;
          animation-duration: 2.5s;
          animation-iteration-count: infinite;
          transition: transform 0.2s linear;
        }
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
        &.psych {
          animation-name: img-psych;
          animation-duration: 2.5s;
          animation-iteration-count: infinite;
          transition: transform 0.2s linear;
        }
      }
    }
    .trio-container {
      background: rgba(0,0,0,0.05);
      padding-top: 1rem;
      padding-bottom: 1rem;
      margin: -$lateral-padding-mobile;
      margin-top: 0;
      margin-bottom: 0;
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
