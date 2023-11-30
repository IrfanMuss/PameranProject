<template>
  <div class="home">
    <div class="hero">
      <h1 class="hero-title">Selamat datang di {{ storeName }}</h1>
      <p class="hero-description">Website Pameran Project IoT</p>
      <NuxtLink to="/product" class="text-base">
        <button class="hero-button">Lihat Project Kami</button>
      </NuxtLink>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      storeName: "Pameran Projeck IoT",
    };
  },
};
</script>

<style scoped>
.home {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
 background-image: url("/images/bg.jpeg");
 background-position: center;
  background-size: cover;
}

.hero {
  text-align: center;
  padding: 40px;
  border-radius: 10px;
  background-color: rgba(255, 255, 255, 0.9);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  backdrop-filter: blur(8px);
}

.hero-title {
  font-size: 3em;
  margin-bottom: 10px;
  color: #007bff;
}

.hero-description {
  font-size: 1.5em;
  color: #333;
  margin-bottom: 30px;
}

.hero-button {
  background-color: #007bff;
  color: #fff;
  border: none;
  padding: 15px 30px;
  font-size: 1.2em;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.hero-button:hover {
  background-color: #0056b3;
}
</style>
