<template>
  <div ref="container"></div>
</template>

<script>
import * as THREE from 'three';

export default {
  mounted() {
    // 创建场景、相机和渲染器
    const scene = new THREE.Scene();
    const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
    const renderer = new THREE.WebGLRenderer();
    renderer.setSize(window.innerWidth, window.innerHeight);
    this.$refs.container.appendChild(renderer.domElement);

    // 创建一个带纹理的球体
    const geometry = new THREE.SphereGeometry(5, 32, 32);
    const texture = new THREE.TextureLoader().load('https://cdn.pixabay.com/photo/2017/08/30/01/05/milky-way-2695569_960_720.jpg');
    const material = new THREE.MeshBasicMaterial({ map: texture });
    const sphere = new THREE.Mesh(geometry, material);
    scene.add(sphere);

    // 创建粒子参数
    const particleCount = 10000;
    const positions = new Float32Array(particleCount * 3);
    const colors = new Float32Array(particleCount * 3);
    let color = new THREE.Color();

    for (let i = 0; i < particleCount; i++) {
      const x = Math.random() * 2000 - 1000;
      const y = Math.random() * 2000 - 1000;
      const z = Math.random() * 2000 - 1000;

      positions[i * 3] = x;
      positions[i * 3 + 1] = y;
      positions[i * 3 + 2] = z;

      color.setHSL(i / particleCount, 1.0, 0.5);

      colors[i * 3] = color.r;
      colors[i * 3 + 1] = color.g;
      colors[i * 3 + 2] = color.b;
    }

    // 创建粒子集合
    const particleGeometry = new THREE.BufferGeometry();
    particleGeometry.setAttribute('position', new THREE.BufferAttribute(positions, 3));
    particleGeometry.setAttribute('color', new THREE.BufferAttribute(colors, 3));
    const particleMaterial = new THREE.PointsMaterial({ size: 15, vertexColors: true });
    const particles = new THREE.Points(particleGeometry, particleMaterial);
    scene.add(particles);

    // 动画循环
    const animate = () => {
      requestAnimationFrame(animate);

      // 更新粒子集合位置
      particles.position.x = sphere.position.x;
      particles.position.y = sphere.position.y;
      particles.position.z = sphere.position.z;

      // 更新粒子集合参数
      particles.material.size = 15;

      // 渲染场景
      renderer.render(scene, camera);
    };
    animate();
  }
};

</script>

<style>
#container {
  margin: 0;
  overflow: hidden;
}
</style>
