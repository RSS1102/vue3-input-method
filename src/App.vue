<script setup lang="ts">
const onMouseLeave = (e: MouseEvent) => {
  console.log("onMouseLeave", e);
};
</script>

<template>
  <div class="card" @mouseleave="onMouseLeave">
    <input type="text" />
    输入框示例
  </div>
</template>

<style scoped>
.card {
  padding: 20px;
  background: #9f8a8a;
}
</style>
