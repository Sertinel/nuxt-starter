<template>
  <div>
    <h3>Mevcut Sayfalar</h3>
    <ul>
      <li v-for="page in pages" :key="page.id">
        {{ page.title }}
        <button @click="$emit('edit', page)">Düzenle</button>
        <button @click="$emit('delete', page.id)">Sil</button>
      </li>
    </ul>
  </div>
</template>

<script setup>
defineProps(['pages'])
defineEmits(['edit', 'delete'])
</script>