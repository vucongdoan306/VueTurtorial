<template>
  <div class="hello-kitty">
    <p id="beforeMount">{{ message }}</p>
    <p v-html="htmlText"></p>
    <button @click="changeTest()" class="btn btn-secondary">
      Thay đổi message
    </button>
    <br /><br /><br /><br />

    <div :class="colorText">Một hai</div>
    <button @click="changeColor()" class="btn btn-secondary">
      Thay đổi màu chữ
    </button>
    <br /><br /><br /><br />

    <select id="province" v-model="selectedProvince">
      <option value="">---Tỉnh/TP---</option>
      <option
        v-for="province in objTest"
        :key="province.code"
        :value="province"
      >
        {{ province.name }}
      </option>
    </select>
    <p>Tôi đến từ {{ selectedProvince.name }}</p>

    <input type="number" v-model="number1" style="margin-right: 10px" />
    <input type="number" v-model="number2" style="margin-right: 10px" />
    <span>Tổng: {{ sum }}</span>
    <br /><br />

    <input
      v-model="firstName"
      placeholder="First Name"
      style="margin-right: 10px"
    />
    <input
      v-model="lastName"
      placeholder="Last Name"
      style="margin-right: 10px"
    />
    <input v-model="fullName" placeholder="Full Name" />
  </div>
</template>

<script>
/* eslint-disable */
import { onMounted } from "vue";
import axios from "axios";
export default {
  props: {
    propInit: {
      type: String,
      default: "hello world",
    },
  },

  beforeCreate() {
    console.log("Beforecreate thì dùng được prop", this.propInit);
    console.log("Còn data thì", this.message);
  },

  created() {
    let me = this;
    console.log("this is created");
    axios.get("https://provinces.open-api.vn/api/p/").then((data) => {
      me.objTest = data.data;
      console.log(me.objTest);
    });
  },

  beforeMount() {
    console.log("Component will beforemount");
  },

  async mounted() {
    console.log("Component mounted");
  },

  beforeUpdate() {
    console.log("Component bèfore updated");
  },

  updated() {
    console.log("Component updated");
  },

  beforeUnmount() {
    console.log("unmount");
  },

  unmounted() {
    console.log(this.message);
  },

  methods: {
    changeTest: function () {
      this.message = this.message + "1";
    },
    changeColor() {
      this.colorText = this.colorText == "red" ? "blue" : "red";
    },
  },

  computed: {
    sum() {
      return this.number1 + this.number2;
    },
    fullName: {
      //getter
      get() {
        return this.firstName + " " + this.lastName;
      },
      // setter
      set(newValue) {
        if (!newValue) newValue = " ";
        [this.firstName, this.lastName] = newValue.split(" ");
      },
    },
  },

  data() {
    return {
      message: "Hello, Vue 3!",
      htmlText: '<span style="color: red">This should be red.</span>',
      colorText: "red",
      objTest: {},
      selectedProvince: "",
      number1: 0,
      number2: 0,
      firstName: "",
      lastName: "",
    };
  },
};
</script>

<style scoped>
.hello-kitty {
  border: 1px solid #000;
  border-radius: 4px;
  margin: 10px 100px;
}
.red {
  color: red;
}

.blue {
  color: blue;
}
</style>
