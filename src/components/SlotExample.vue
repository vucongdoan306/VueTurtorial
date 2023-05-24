<!-- SlotExample.vue -->
<template>
  <div class="product-card">
    <slot name="title"></slot>
    <!-- <slot name="title" :text="year"></slot> -->
    <slot name="description"></slot>
    <slot name="price"></slot>
  </div>
</template>

<script>
export default {
  name: "SlotExample",
  data() {
    return {
      year: 2023,
    };
  },
};
</script>
<style scoped>
.product-card {
  border: 1px solid #000;
  border-radius: 4px;
  padding: 10px;
}
</style>
