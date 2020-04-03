<template>
  <div id="app">
    <div class="primaryView">
      <img class="app-logo" src="./assets/jmi-logo.png" />
      <form v-if="!formIsSubmitted" @submit.prevent="handleSubmit">
        <ul>
          <li>
            <input type="text" v-model="form.insuredName" placeholder="Insured Name" />
          </li>
          <li>
            <input type="text" v-model="form.insuredItem" placeholder="Insured Item" />
          </li>
          <li>
            <input
              type="text"
              name="insured_value"
              v-model="form.insuredValue"
              placeholder="Insured Item Value"
            />
          </li>
          <li>
            <input
              type="text"
              v-model="form.insuredIncome"
              v-if="form.insuredValue >= 10000"
              placeholder="Annual Income"
            />
          </li>
          <li>
            <button type="submit" class="open">Submit</button>
          </li>
        </ul>
      </form>
    </div>
    <!-- <div class="secondaryView">Hello World</div> -->
  </div>
</template>

<script>
export default {
  name: 'app',
  data() {
    return {
      formIsSubmitted: false,
      // insuredName: '',
      // insuredItem: '',
      // insuredValue: '',
      // insuredIncome: '',
      // submitMessage: 'Thank you!',
      form: {
        insuredName: '',
        insuredItem: '',
        insuredValue: '',
        insuredIncome: '',
        submitMessage: 'Thank you!'
      }
    };
  },
  methods: {
    handleSubmit() {
      console.log({
        greet: this.form.submitMessage,
        name: this.form.insuredName,
        item: this.form.insuredItem,
        value: this.form.insuredValue,
        income: this.form.insuredIncome
      });
    }
  }
};
</script>

<style>
.primaryView {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: grid;
  min-height: 100vh;
  place-items: center;
  background: whitesmoke;
  justify-items: stretch;
  font-family: "Avenir";
  font-weight: normal;
  font-style: normal;
  line-height: 1.4;
}

.secondaryView {
}

.app-logo {
  position: absolute;
  width: 200px;
  left: 50%;
  right: 50%;
  margin-left: -100px;
  margin-right: -100px;
  margin-top: 20px;
}

h1,
h2 {
  font-weight: normal;
}

input,
button {
  font: inherit;
  border: 0;
}

input:focus,
button:focus {
  outline: none;
}

form {
  display: flex;
  grid-column: 2;
}

input {
  flex-grow: 1;
  padding: 0.8em 1.5em;
}

button {
  padding: 0.5em 0.75em;
  background: #159ad7;
  width: 100%;
}

ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
  display: inline-block;
}
</style>