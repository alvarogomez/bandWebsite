<template>
  <div id="app" ref="appCont">
    <router-view/>
  </div>
</template>

<script>

export default {
  name: 'App',
  mounted() {
    setInterval(this.updateGradient, 10);
    this.$eventBus.$on('enter-psychedelic-mode', () => {
      if (!this.psychedelicMode) {
        this.psychedelicMode = true;
        let backupSpeed = this.gradientSpeed;
        this.gradientSpeed = 0.050;
        var self = this;
        setTimeout(function(){
          self.gradientSpeed = backupSpeed;
          self.psychedelicMode = false;
        }, 5000)
      }
    });
  },
  data() {
    return {
      gradient: '',
      gradientSpeed: 0.003,
      psychedelicMode: false,
      step: 0,
      colorIndices : [0, 1, 2, 3],
      colors : [[247, 23, 53], [65, 234, 212], [255, 159, 28], [230, 232, 230]]
    };
  },
  methods: {
    updateGradient() {

      let c0_0 = this.colors[this.colorIndices[0]];
      let c0_1 = this.colors[this.colorIndices[1]];
      let c1_0 = this.colors[this.colorIndices[2]];
      let c1_1 = this.colors[this.colorIndices[3]];

      let istep = 1 - this.step;
      const opacity = 0.7;
      let r1 = Math.round(istep * c0_0[0] + this.step * c0_1[0]);
      let g1 = Math.round(istep * c0_0[1] + this.step * c0_1[1]);
      let b1 = Math.round(istep * c0_0[2] + this.step * c0_1[2]);
      let color1 = `rgba(${r1},${g1},${b1},${opacity})`;

      let r2 = Math.round(istep * c1_0[0] + this.step * c1_1[0]);
      let g2 = Math.round(istep * c1_0[1] + this.step * c1_1[1]);
      let b2 = Math.round(istep * c1_0[2] + this.step * c1_1[2]);
      let color2 = `rgba(${r2},${g2},${b2},${opacity})`;

      let app = document.querySelector('#app');

      this.$refs.appCont.style.background = 'repeating-radial-gradient(' + color1 + ',' + color2 + ')';
      this.step += this.gradientSpeed;

      if (this.step >= 1) {
        this.step %= 1;
        this.colorIndices[0] =this.colorIndices[1];
        this.colorIndices[2] = this.colorIndices[3];
        this.colorIndices[1] = (this.colorIndices[1] + Math.floor(1 + Math.random() * (this.colors.length - 1))) % this.colors.length;
        this.colorIndices[3] = (this.colorIndices[3] + Math.floor(1 + Math.random() * (this.colors.length - 1))) % this.colors.length;
      }
    }
  }
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Roboto:400,700|Bungee+Shade:400,700');
@import 'variables';
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background: rgba(20,218,209,0.2);
  width: 100%;
  padding: 0px;
  margin: 0px;
  min-height: 100vh;
}
html {
  height: 100%;
}
body {
  margin: 0;
  min-height: 100%;
  position: relative;
}
* {
  box-sizing: border-box;
}
</style>
