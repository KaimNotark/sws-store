<template>
  <div class="parallax-container">
    <section class="main">
      <div class="wrap wrap--1">
        <div
          v-bind:style="{ 
          backgroundPosition: styleObject.bX +' '+ styleObject.bY,
          transform: 'rotate(' + styleObject.rX + ') rotateY('+ styleObject.rY + ')'
           }"
          class="container container--1"
          @mousemove="handleMouseMove"
          @mouseleave="handleMouseLeave"
        ></div>
      </div>
    </section>
  </div>
</template>
    
<script>
export default {
  name: "Parallax",

  data() {
    return {
      styleObject: {
        rX: "0deg",
        rY: "0deg",
        bX: "50%",
        bY: "80%"
      }
    };
  },

  methods: {
    handleMouseMove(event) {
      const { offsetX, offsetY } = event;
      let X;
      let Y;

      X = -(offsetX - 150) / 3 / 3;
      Y = (offsetY - 180) / 3 / 3;

      this.styleObject.rY = X.toFixed(2) + "deg";
      this.styleObject.rX = Y.toFixed(2) + "deg";

      this.styleObject.bY = 80 - (X / 4).toFixed(2) + "%";
      this.styleObject.bX = 80 - (Y / 4).toFixed(2) + "%";
    },

    handleMouseLeave() {
      this.styleObject.rY = "0deg";
      this.styleObject.rX = "0deg";
      this.styleObject.bY = "80%";
      this.styleObject.bX = "50%";
    }
  }
};
</script>

<style lang="scss" scoped>
*,
*::after,
*::before {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.main {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
}

.wrap {
  margin: 2rem;
  transform-style: preserve-3d;
  transform: perspective(100rem);
  cursor: pointer;
}

.container {
  width: 30rem;
  height: 36rem;
  border: 2px solid red;
  border-radius: 1.6rem;
  padding: 4rem;
  display: flex;
  align-items: flex-end;
  position: relative;
  background: linear-gradient(hsla(0, 0%, 100%, 0.1), hsla(0, 0%, 100%, 0.3)),
    url("/images/ship-logo.png");
  background-size: 10rem auto;
  box-shadow: 0 0 3rem 0.5rem hsla(0, 0%, 0%, 0.2);
  transition: transform 0.6s 1s;
}

.container::before,
.container::after {
  content: "";
  width: 2rem;
  height: 2rem;
  border: 2px solid red;
  position: absolute;
  z-index: 2;
  opacity: 0.3;
  transition: 0.3s;
}

.container::before {
  top: 2rem;
  right: 2rem;
  border-bottom-width: 0;
  border-left-width: 0;
}

.container::after {
  bottom: 2rem;
  left: 2rem;
  border-top-width: 0;
  border-right-width: 0;
}

.wrap:hover .container::before,
.wrap:hover .container::after {
  width: calc(100% - 4rem);
  height: calc(100% - 4rem);
}
</style>