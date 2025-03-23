<script setup>
import { ref } from 'vue'

const showDetails = ref(false);

defineProps({
  user: {
    type: Object,
    default: () => ({}),
  }
})

const toggleDetails = () => {
  showDetails.value = !showDetails.value
}
</script>

<template>
  <div class="userItem">
    <div class="userInfo">
      <strong>{{ user.name }}</strong>
      <button @click="toggleDetails" class="detailsBtn">
        <strong>{{ showDetails ? 'Сховати' : 'Показати' }} Деталі</strong>
      </button>
    </div>
    <div class="userDetails" :class="{show: showDetails}">
      <p>Email: {{ user.email }}</p>
      <p>Телефон: {{ user.phone }}</p>
    </div>
  </div>
</template>
