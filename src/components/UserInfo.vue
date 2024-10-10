<template>
  <div class="user-info">
    <img :src="userIcon" alt="User Icon">
    <span>{{ userName }}</span>
  </div>
</template>

<script lang="js">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'UserInfo',
  data() {
    return {
      userIcon: 'https://www.iconpacks.net/icons/2/free-user-icon-3296-thumb.png',
      userName: 'John Doe',
    };
  },
});
</script>

<style scoped>
/* Add user info styles here */
</style>