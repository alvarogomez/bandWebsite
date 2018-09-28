<template lang="html">

  <section class="navigation-header">
    <div class="hamburger" @click="clickedHamburger()">
      <div id="nav-icon2" v-bind:class="{ open : isUncollapsed }">
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
      </div>
    </div>
    <div v-bind:class="{ psych: psychedelicMode }" class="mushroom" v-on:click="clickedMushroom">
      <img src="../assets/mushroom.png" alt="mushroom">
    </div>
    <transition name="slide">
      <div v-if="isUncollapsed" class="menu-wrapper">
        <ul>
          <li>
            <a href="#">Bio</a>
          </li>
          <li>
            <a href="#">Music</a>
          </li>
          <li>
            <a href="#">Video</a>
          </li>
          <li>
            <a href="#">Photos</a>
          </li>
          <li>
            <a href="#">Rider</a>
          </li>
          <li>
            <a href="#">Contact</a>
          </li>
          <li>
            <a href="#">About</a>
          </li>
        </ul>
      </div>
    </transition>
  </section>

</template>

<script lang="js">
export default {
  name: 'navigation-header',
  props: ['iconType'],
  mounted() {
    this.$eventBus.$on('enter-psychedelic-mode', () => {
      this.psychedelicMode = true;
      var self = this;
      setTimeout(function(){
        self.psychedelicMode = false;
      }, 5000)
    });
  },
  data() {
    return {
      collapsed: false,
      psychedelicMode: false,
    };
  },
  methods: {
    clickedHamburger() {
      this.collapsed = !this.collapsed;
    },
    clickedMushroom() {
      this.$eventBus.$emit('enter-psychedelic-mode');
    }
  },
  computed: {
    isUncollapsed() {
      return this.collapsed;
    }
  }
};
</script>

<style scoped lang="scss">
@import '../variables';
  .navigation-header {
    z-index: 2;
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
      &.psych {
        animation-name: mushroom-psych;
        animation-duration: 0.5s;
        animation-iteration-count: infinite;
        transition: transform 0s ease-in-out;
      }
      img {
        width: 100%;
      }
    }
    .menu-wrapper {
      position: absolute;
      top: 60px;
      left: 0;
      width: 50vw;
      background-color: rgba(0,0,0,0.8);
      height: calc(100vh - 60px);
      a {
        text-decoration: none;
        color: #FEFEFE;
        font-size: 22px;
        line-height: 40px;
        text-align: left;
        display: block;
      }
      ul {
        padding: $lateral-padding-mobile;
        li {
          margin: 1rem 0;
          border-bottom: 1px dotted $grey-silver;
        }
      }
    }
  }
  .slide-enter-active {
    animation: bounce-in .5s;
    transition: all .4s cubic-bezier(1.0, 0.5, 0.8, 1.0);
  }
  .slide-leave-active {
    animation: bounce-in .5s reverse;
    transition: all .4s cubic-bezier(1.0, 0.5, 0.8, 1.0);
  }
  @keyframes bounce-in {
    0% {
      opacity:  0;
      transform: translateX(-50vw);
    }
    100% {
      opacity:  0.9;
      transform: translateX(0vw);;
    }
  }
  @keyframes mushroom-anim {
    0% { transform: scale(1) }
    50% { transform: scale(1.1) }
    100% { transform: scale(1) }
  }
  @keyframes mushroom-psych {
    0% {
      color: red;
      transform: scale(1) rotateZ(0deg);
    }
    50% {
      transform: scale(1.5) rotateZ(180deg);
    }
    100% {
      transform: scale(1) rotateZ(360deg);
    }
  }
</style>
