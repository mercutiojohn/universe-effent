<template>
  <div class="time-travel">
    <div class="time-travel__background">
      <div class="time-travel__stars"></div>
      <div class="time-travel__nebula"></div>
      <div class="time-travel__vortex">
        <div class="time-travel__vortex-inner"></div>
      </div>
    </div>
    <div class="time-travel__ship"></div>
  </div>
</template>

<style>
.time-travel {
  position: relative;
  width: 100%;
  height: 100vh;
  overflow: hidden;
}

.time-travel__background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: black;
  overflow: hidden;
}

.time-travel__stars {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: url("https://cdn.pixabay.com/photo/2013/07/18/10/56/starry-sky-163631_960_720.jpg");
  background-repeat: repeat;
  animation: stars 60s linear infinite;
}

.time-travel__nebula {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: url("https://cdn.pixabay.com/photo/2017/08/30/01/05/milky-way-2695569_960_720.jpg");
  background-repeat: repeat;
  animation: nebula 120s linear infinite;
}

.time-travel__vortex {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 500px;
  height: 500px;
  margin-top: -250px;
  margin-left: -250px;
  border-radius: 50%;
  border: 10px solid rgba(255, 255, 255, 0.5);
  overflow: hidden;
  animation: vortex 30s ease-in-out infinite;
}

.time-travel__vortex-inner {
  position: absolute;
  top: -600px;
  left: -600px;
  width: 2400px;
  height: 2400px;
  background-image: url("https://cdn.pixabay.com/photo/2017/08/30/01/05/milky-way-2695569_960_720.jpg");
  background-repeat: repeat;
  border-radius: 50%;
  animation: vortex-inner 30s ease-in-out infinite;
}

.time-travel__ship {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 120px;
  height: 120px;
  margin-top: -60px;
  margin-left: -60px;
  background-image: url("https://cdn.pixabay.com/photo/2016/01/19/17/09/spaceship-1149559_960_720.png");
  background-size: contain;
  animation: ship 30s ease-in-out infinite;
}

@keyframes stars {
  0% {
    background-position: 0 0;
  }
  100% {
    background-position: 10000px 0;
  }
}

@keyframes nebula {
  0% {
    background-position: 0 0;
  }
  100% {
    background-position: 0 -10000px;
  }
}

@keyframes vortex {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

@keyframes vortex-inner {
  0% {
    background-position: 0 0;
  }
  100% {
    background-position: 10000px 0;
  }
}

@keyframes ship {
  0% {
    transform: translate(-50%, -50%) rotate(0deg) scale(1);
  }
  50% {
    transform: translate(-50%, -50%) rotate(180deg) scale(2);
  }
  100% {
    transform: translate(-50%, -50%) rotate(360deg) scale(1);
  }
}
</style>
