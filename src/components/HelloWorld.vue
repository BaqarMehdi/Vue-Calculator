<template>
  <div class="calculator-wraper">
    <div class="calculator-container">
      <div class="input">
        <input type="text" v-model="display" />
      </div>
      <div class="btns row-1">
        <button @click="ondisplay('7')">7</button>
        <button @click="ondisplay('8')">8</button>
        <button @click="ondisplay('9')">9</button>
        <button @click="ondisplay('-')">-</button>
      </div>
      <div class="btns row-2">
        <button @click="ondisplay('4')">4</button>
        <button @click="ondisplay('5')">5</button>
        <button @click="ondisplay('6')">6</button>
        <button @click="ondisplay('/')">/</button>
      </div>
      <div class="btns row-3">
        <button @click="ondisplay('1')">1</button>
        <button @click="ondisplay('2')">2</button>
        <button @click="ondisplay('3')">3</button>
        <button @click="ondisplay('*')">*</button>
      </div>
      <div class="btns row-4">
        <button @click="deletecontent()">C</button>
        <button @click="ondisplay('0')">0</button>
        <button @click="evaluate()">=</button>
        <button @click="ondisplay('+')">+</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      display: "",
    };
  },
  methods: {
    ondisplay(value) {
      if (this.display === "Error") {
        this.display = "";
      }
      this.display += value;
    },
    evaluate() {
      try {
        this.display = eval(this.display);
      } catch (error) {
        this.display = "Error";
        console.error("Evaluation error:", error);
      }
    },
    deletecontent() {
      this.display = "";
    },
  },
};
</script>

<style>
.calculator-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  /* height: 100vh; */
  /* width: 100vw; */
}

.calculator-container {
  background-color: gray;
  width: 230px; /* Adjust the width as per your requirement */
  padding: 20px; /* Add some padding for better aesthetics */
}
input {
  border-radius: 0.5rem;
  border-color: none;
  padding: 0.4rem;
  color: black;
}
.btns {
  margin: 1rem;
}
button {
  background-color: rgb(46, 45, 45);
  color: white;
  margin: 0 0.4rem;
  padding: 0.6rem 0.7rem;
}
</style>
