<template>
  <canvas ref="myCanvas"></canvas>
</template>

<script>
export default {
  mounted() {
    const myCanvas = this.$refs.myCanvas;
    const ctx = myCanvas.getContext("2d");
    const starList = [];

    function init() {
      myCanvas.width = window.innerWidth;
      myCanvas.height = window.innerHeight;
    }
    init();

    window.addEventListener("resize", init);

    function Star(x, y, radius, disX, disY, opa) {
      this.x = x;
      this.y = y;
      this.radius = radius;
      this.disX = disX;
      this.disY = disY;
      this.opacity = opa;
    }

    for (let i = 0; i < 800; i++) {
      const x = Math.random() * myCanvas.width;
      const y = Math.random() * myCanvas.height;
      const radius = Math.random() * 2;
      const disX = x - myCanvas.width / 2;
      const disY = y - myCanvas.height / 2;
      const opacity = 0;
      starList.push(new Star(x, y, radius, disX, disY, opacity));
    }

    function animate() {
      ctx.clearRect(0, 0, myCanvas.width, myCanvas.height);

      for (let i = 0; i < 800; i++) {
        const a = starList[i];

        a.x += a.disX / 50;
        a.y += a.disY / 50;
        a.opacity += 0.1;

        if (
          a.x < 0 ||
          a.y < 0 ||
          a.x > myCanvas.width ||
          a.y > myCanvas.height
        ) {
          a.x = Math.random() * myCanvas.width;
          a.y = Math.random() * myCanvas.height;
          a.disX = a.x - myCanvas.width / 2;
          a.disY = a.y - myCanvas.height / 2;
          a.opacity = 0;
        }

        ctx.beginPath();
        // ctx.fillStyle = "#ffffff";
        ctx.fillStyle = "rgba(255, 255, 255, " + a.opacity + ")";
        ctx.arc(a.x, a.y, a.radius, 0, Math.PI * 2, false);
        ctx.fill();
      }

      setTimeout(animate, 40);
    }

    animate();
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

html,
body {
  width: 100vw;
  height: 100vh;
  overflow: hidden;
}
</style>
<style scoped>
canvas {
  background-color: #000;
  width: 100%;
  height: 100%;
}
</style>
