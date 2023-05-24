<template>
  <div class="watch-example d-flex justify-content-evenly mt-5 mb-5">
    <div class="normal-watch">
        <h1>Watch thường</h1>
      <div class="title">Number 1</div>
      <input type="number" name="" id="" v-model="number1" />

      <div class="title">Chẵn hay lẻ?</div>
      <input type="text" name="" id="" v-model="result" readonly />
    </div>

    <div class="deep-watch">
        <h1>Deep Watch</h1>
      <div>
        <p>Kết quả: {{ deepObj.upper }}</p>
        <input ref="input1" v-model="deepObj.nestedProp" placeholder="Nhập một giá trị" />
      </div>

      <button @click="$emit('show-loading')" class="btn btn-success mt-3"> Hiện loading</button>
    </div>

    
  </div>
</template>
<script>
export default {
    emits: ['show-loading'],
    mounted() {
        this.$refs.input1.focus();
    },
  watch: {
    number1(newVal) {
      this.result = newVal % 2 == 0 ? "chẵn" : "lẻ";
    },
    deepObj: {
      handler(newValue) {
        this.deepObj.upper = newValue.nestedProp.toUpperCase();
      },
      deep: true,
    },
  },
  data() {
    return {
      number1: 0,
      result: "chẵn",
      deepObj: {
        nestedProp: "",
        upper:""
      },
    };
  },
  
};
</script>
<style lang="css">
.watch-example{
  border: 1px solid #000;
  border-radius: 4px;
  margin:10px 100px;
  padding: 10px;
}
</style>
