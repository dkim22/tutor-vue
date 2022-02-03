<template>
  <div class="business-card">
    <div v-for="user in users" :key="user.id" class="business-card__wrapper">
      <div class="business-card__name">Name: {{ user.name }}</div>
      <div class="business-card__username">NickName: {{ user.username }}</div>
      <div class="business-card__email">Email: {{ user.email }}</div>
      <div class="business-card__phone">Phone: {{ user.phone }}</div>
      <div class="business-card__company-name">
        Company: {{ user.company.name }}
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, onMounted, ref } from "vue";

export default defineComponent({
  setup() {
    const users = ref([]);

    const getUsers = async () => {
      const response = await fetch(
        `https://jsonplaceholder.typicode.com/users`
      );
      const data = await response.json();
      users.value = data;
    };

    onMounted(getUsers);

    return { users };
  },
});
</script>

<style scoped lang="scss">
.business-card {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 16px;
  margin-top: 24px;

  &__wrapper {
    border: 1px solid #000;
    background-color: #f2f2f2;
    border-radius: 3px;
    flex: 0 0 250px;
    padding: 8px 16px;
  }
}
</style>
