<template>
  <div>
    <h3>{{ isEditing ? 'Sayfayı Düzenle' : 'Yeni Sayfa Ekle' }}</h3>
    <form @submit.prevent="submitForm">
      <input v-model="form.title" placeholder="Sayfa Başlığı" required />
      <textarea v-model="form.content" placeholder="Sayfa İçeriği" required></textarea>
      <button type="submit">{{ isEditing ? 'Güncelle' : 'Ekle' }}</button>
      <button v-if="isEditing" type="button" @click="cancelEdit">İptal</button>
    </form>
  </div>
</template>

<script setup>
import { ref, reactive, watch } from 'vue'

const props = defineProps({
  pageToEdit: { type: Object, default: null }
})

const emit = defineEmits(['add', 'update'])

const isEditing = ref(false)
const form = reactive({
  title: '',
  content: ''
})

const resetForm = () => {
  form.title = ''
  form.content = ''
  isEditing.value = false
}

const submitForm = () => {
  if (isEditing.value) {
    emit('update', { ...props.pageToEdit, ...form })
  } else {
    emit('add', { ...form })
  }
  resetForm()
}

const cancelEdit = () => {
  resetForm()
  emit('update', null)
}

watch(() => props.pageToEdit, (newVal) => {
  if (newVal) {
    form.title = newVal.title
    form.content = newVal.content
    isEditing.value = true
  } else {
    resetForm()
  }
}, { immediate: true })
</script>