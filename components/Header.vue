<script lang="ts" setup>
import { useAuthStore } from "~/stores/auth";
const authStore = useAuthStore();
const isAuthenticated = ref();
const router = useRouter();
isAuthenticated.value = useCookie("access_token").value;
const logout = async () => {
  await authStore.logout();
  const accessToken = useCookie("access_token");
  const refreshToken = useCookie("refresh_token");
  accessToken.value = null;
  refreshToken.value = null;
  setTimeout(() => {
    isAuthenticated.value = useCookie("access_token").value;
  }, 100);
  router.push({
    path: "/",
  });
};
</script>
<template>
  <header class="bg-gray-800 p-4 flex justify-between items-center text-white">
    <div class="container">
      <div class="flex justify-between items-center">
        <div>
          <NuxtLink to="/" class="text-xl font-bold">Vann Kang IoT🗿</NuxtLink>
        </div>
        <nav class="flex items-center gap-6">
          <NuxtLink to="/" class="text-base">🏚</NuxtLink>

          <NuxtLink to="/product" class="text- base">🖥️</NuxtLink>

          <NuxtLink to="/about" class="text-base">⚠</NuxtLink>

         <NuxtLink
            v-if="!isAuthenticated"
            to="/login"
            class="text-base bg-blue-600 px-6 py-2 text-white rounded-lg hover:bg-blue-600/80"
            >🚪</NuxtLink
          >
          <div
            v-else
            class="text-base cursor-pointer bg-red-600 px-6 py-2 text-white rounded-lg hover:bg-red-600/80"
            @click="logout"
          >
          📥
          </div>
        </nav>
      </div>
    </div>
  </header>
</template>

tolong ubah header home menjadi logo rumah, dan header produk menjadi logo produk,dan headder cart menjadi logo keranjang menggunkan tailwindcss


<style scoped>
header {
  background-color: blue;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

.logo {
  font-size: 1.5rem;
  font-weight: bold;
}

nav {
  display: flex;
  align-items: center;
}

nav a {
  color: #fff;
  text-decoration: none;
  font-size: 1rem;
  transition: color 0.3s ease;
}

nav a:hover {
  color: #ffd700; /* Warna kuning untuk efek hover */
}

.auth-button {
  display: inline-block;
  padding: 8px 16px;
  border-radius: 5px;
  text-decoration: none;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.auth-button.login {
  background-color: #3490dc; /* Warna biru untuk tombol login */
  color: #fff;
}

.auth-button.logout {
  background-color: #e53e3e; /* Warna merah untuk tombol logout */
  color: #fff;
}

.auth-button:hover {
  background-color: rgba(255, 215, 0, 0.8); /* Warna kuning untuk efek hover */
}
</style>
