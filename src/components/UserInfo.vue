<template>
  <div class="user-info">
    <img :src="userIcon" alt="User Icon" :width="30" :height="30">
    <span>{{ userName }}</span>
  </div>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'UserInfo',
  data() {
    return {
      userIcon: 'https://www.iconpacks.net/icons/2/free-user-icon-3296-thumb.png',
      userName: 'Alexander Borisenko',
    };
  },
});
</script>

<style scoped>
/* Add user info styles here */
.user-info {
  display: flex;
  align-items: center;
}
img {
  margin-right: 5px;
}
</style>