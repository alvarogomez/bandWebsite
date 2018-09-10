<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
// var colors = new Array([190, 149, 196], [159, 134, 192], [94, 84, 142], [224, 177, 203]);
// const colors = new Array([255, 89, 94], [255, 202, 58], [138, 201, 38], [25, 130, 196]);
// const colors = new Array([20, 218, 209], [156, 174, 169], [120, 133, 133], [160, 141, 186]);
const colors = new Array([247, 23, 53], [65, 234, 212], [255, 159, 28], [230, 232, 230]);

let step = 0;
//color table indices for:
// current color left
// next color left
// current color right
// next color right
const colorIndices = [0, 1, 2, 3];

//transition speed
const gradientSpeed = 0.003;

function updateGradient() {
  let c0_0 = colors[colorIndices[0]];
  let c0_1 = colors[colorIndices[1]];
  let c1_0 = colors[colorIndices[2]];
  let c1_1 = colors[colorIndices[3]];

  let istep = 1 - step;
  const opacity = 0.7;
  let r1 = Math.round(istep * c0_0[0] + step * c0_1[0]);
  let g1 = Math.round(istep * c0_0[1] + step * c0_1[1]);
  let b1 = Math.round(istep * c0_0[2] + step * c0_1[2]);
  let color1 = `rgba(${r1},${g1},${b1},${opacity})`;

  let r2 = Math.round(istep * c1_0[0] + step * c1_1[0]);
  let g2 = Math.round(istep * c1_0[1] + step * c1_1[1]);
  let b2 = Math.round(istep * c1_0[2] + step * c1_1[2]);
  let color2 = `rgba(${r2},${g2},${b2},${opacity})`;

  let app = document.querySelector('#app');
  app.style.background = '-webkit-gradient(linear, left top, right bottom, from(' + color1 + '), to(' + color2 + '))';
  app.style.background = '-moz-linear-gradient(left, ' + color1 + ' 0%, ' + color2 + ' 100%)';

  step += gradientSpeed;
  if (step >= 1) {
    step %= 1;
    colorIndices[0] = colorIndices[1];
    colorIndices[2] = colorIndices[3];

    //pick two new target color indices
    //do not pick the same as the current one
    colorIndices[1] = (colorIndices[1] + Math.floor(1 + Math.random() * (colors.length - 1))) % colors.length;
    colorIndices[3] = (colorIndices[3] + Math.floor(1 + Math.random() * (colors.length - 1))) % colors.length;
  }
}

setInterval(updateGradient, 10);

export default {
  name: 'App'
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
  color: #444;
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
