<script setup>
import {onMounted, ref} from "vue";
import User from "./components/User.vue";
import Preloader from "./components/Preloader.vue";

const users = ref([]);
const isLoading = ref(true);

const fetchUsers = async () => {
  try {
    users.value = await fetch('https://jsonplaceholder.typicode.com/users')
      .then((response) => response.json());
  } catch (error) {
    console.error('Error fetching users:', error);
  } finally {
    isLoading.value = false;
  }
};

onMounted(() => {
  fetchUsers();
});
</script>

<template>
  <div class="appContainer">
    <div class="contentWr">
      <header class="header">
        <div class="dFjCaC">
          <h1>Список користувачів</h1>
        </div>
      </header>

      <div class="mainLayout">
        <main class="content">
          <preloader v-if="isLoading" />
          <div class="usersWr">
            <user
                v-for="user in users"
                :key="user.id"
                :user="user"
            />
          </div>
        </main>

        <aside class="sidebar">
          <h2>Сайдбар</h2>
        </aside>
      </div>

      <footer class="footer">
        <p>©{{ new Date().getFullYear() }} PayFlow</p>
      </footer>
    </div>
  </div>
</template>

<style scoped>

</style>
