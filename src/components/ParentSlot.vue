<template>
  <div class="slot-example">
    <h2>Thông tin sản phẩm</h2>
    <div class="d-flex justify-content-evenly flex-wrap">
      <SlotExample v-for="product in productList" :key="product.title" class="mx-3">
        <template #title>
          <h3>{{ product.title }}</h3>
        </template>
        <!-- <template #title="{text}">
          <h3>{{ product.title + " " + text}}</h3>
        </template> -->
        <template #description>
          <p>{{ product.description }}</p>
        </template>
        <template #price>
          <p>Giá: {{ product.price }}</p>
        </template>
      </SlotExample>
    </div>
  </div>
</template>

<script>
import SlotExample from "./SlotExample.vue";

export default {
  components: {
    SlotExample,
  },
  data() {
    return {
      productList: [
        {
          title: "Sản phẩm A",
          description: "Mô tả sản phẩm A",
          price: 100,
        },
        {
          title: "Sản phẩm A1",
          description: "Mô tả sản phẩm A1",
          price: 5460,
        },
        {
          title: "Sản phẩm BC",
          description: "Mô tả sản phẩm BC",
          price: 1020,
        },
        {
          title: "Sản phẩm AĂÂ",
          description: "Mô tả sản phẩm AĂÂ",
          price: 3010,
        },
        {
          title: "Sản phẩm VCDOAN",
          description: "Mô tả sản phẩm VCDOAN",
          price: 3280,
        },
        {
          title: "Sản phẩm Vue",
          description: "Mô tả sản phẩm Vue",
          price: 12380,
        },
      ],
    };
  },
};
</script>
<style lang="css">
.slot-example{
  border: 1px solid #000;
  border-radius: 4px;
  margin:30px 100px;
  padding: 30px;
}
</style>