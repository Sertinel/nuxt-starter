<template>
  <nav>
    <ul>
      <li><NuxtLink to="/">Ana Sayfa</NuxtLink></li>
      <li><NuxtLink to="/about">Hakkımızda</NuxtLink></li>
      <li><NuxtLink to="/contact">İletişim</NuxtLink></li>
      <li><NuxtLink to="/admin">Yönetim</NuxtLink></li>
    </ul>
  </nav>
</template>

<script setup>
// Navbar logic can be added here if needed
</script>

<style scoped>
nav ul {
  list-style-type: none;
  padding: 0;
}
nav ul li {
  display: inline;
  margin-right: 10px;
}
a {
  color: #00c58e;
  text-decoration: none;
}
a:hover {
  text-decoration: underline;
}
</style>