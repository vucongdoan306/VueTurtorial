<template>
  <div>
    <!-- Vòng đời vue -->
    <div>
      <button @click="showH = !showH" class="btn btn-primary">
        {{ showH ? "Hủy component 1" : "Hiện component 1" }}
      </button>
      <HelloWorld v-if="showH" class="pb-5" />
    </div>

    <!-- watch -->
    <div>
      <button @click="showW = !showW" class="btn btn-primary mt-5">
        {{ showW ? "Hủy component 2" : "Hiện component 2" }}
      </button>
      <TheWatch v-if="showW" @show-loading="showLoading = true" />
    </div>

    <div class="mt-5"></div>

    <TheLoading v-if="showLoading" />
    <button @click="showLoading = true" class="btn btn-success">Hiện loading</button>

    <!-- props -->
    <div class="mt-5">
      <button @click="showP = !showP" class="btn btn-primary">
        {{ showP ? "Hủy component 3" : "Hiện component 3" }}
      </button>
      <div class="example-prop" v-if="showP">
        <div class="form-input">
          <BaseInput :placeholder="'Input một dòng'" />
        </div>
        <div class="form-input">
          <BaseInput :placeholder="'Input nhiều dòng'" :is-multiple="true" />
        </div>
        <div class="form-input">
          <BaseInput :placeholder="'Input số'" :type="'number'" />
        </div>
      </div>
    </div>

    <!-- slot -->
    <div class="mt-5">
      <button @click="showS = !showS" class="btn btn-primary">
        {{ showS ? "Hủy component 4" : "Hiện component 4" }}
      </button>
      <parent-slot v-if="showS"></parent-slot>
    </div>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import TheWatch from "./components/TheWatch.vue";
import BaseInput from "./components/BaseInput.vue";
import TheLoading from "./components/TheLoading.vue";
import ParentSlot from "./components/ParentSlot.vue";
export default {
  name: "App",
  components: {
    HelloWorld,
    TheWatch,
    TheLoading,
    BaseInput,
    ParentSlot,
  },
  watch: {
    showLoading() {
      setTimeout(() => {
        this.showLoading = false;
      }, 1000);
    },
  },
  data() {
    return {
      showH: false,
      showW: false,
      showP: false,
      showS: false,
      showLoading: false,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.example-prop {
  border: 1px solid #000;
  border-radius: 4px;
  padding: 10px;
  margin: 100px;
}

.form-input {
  width: 100%;
  margin-bottom: 20px;
  display: flex;
  justify-content: center;
}
</style>
