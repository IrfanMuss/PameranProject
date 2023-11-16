<template>
  <div class="home">
    <div class="hero">
      <h1 class="hero-title">Selamat datang di {{ storeName }}</h1>
      <p class="hero-description">Temukan produk berkualitas di toko kami.</p>
      <NuxtLink to="/product" class="text-base">
        <button class="hero-button">Lihat Produk Kami</button>
      </NuxtLink>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      storeName: "Vann Store",
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
  background: url("images/bg.jpg") center/cover no-repeat;
}

.hero {
  text-align: center;
  padding: 40px;
  border-radius: 10px;
  background-color: rgba(255, 255, 255, 0.8);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.hero-title {
  font-size: 2.5em;
  margin-bottom: 10px;
  color: #007bff;
}

.hero-description {
  font-size: 1.5em;
  color: #555;
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
