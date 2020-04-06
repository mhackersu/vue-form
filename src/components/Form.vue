<template>
  <div id="register-form">
    <div class="primaryView" v-if="!isSubmitted">
      <img class="app-logo" src="./assets/jmi-logo.png" />
      <form v-if="!formIsSubmitted" @submit.prevent="handleSubmit">
        <ul>
          <li>
            <input type="text" v-model="form.insuredName" placeholder="Insured Name" />
          </li>
          <li>
            <input v-model="form.insuredItem" type="text" placeholder="Insured Item" />
          </li>
          <li>
            <input
              v-model="form.insuredValue"
              type="text"
              name="insured_value"
              placeholder="Insured Item Value"
            />
          </li>
          <li>
            <input
              v-if="form.insuredValue >= 10000"
              v-model="form.insuredIncome"
              type="text"
              placeholder="Annual Income"
            />
          </li>
          <li>
            <button type="submit" class="open">Submit</button>
          </li>
        </ul>
      </form>
    </div>
    <div class="secondaryView" v-else>
      <img class="app-logo" src="./assets/jmi-logo.png" />
      <form @submit.prevent="handleReset">
        <ul>
          <li>
            <input type="text" placeholder="Items you submitted:" />
          </li>
          <li>
            <input type="text" v-model="form.insuredName" />
          </li>
          <li>
            <input v-model="form.insuredItem" type="text" />
          </li>
          <li>
            <input v-model="form.insuredValue" type="text" />
          </li>
          <li>
            <input v-model="form.insuredIncome" type="text" />
          </li>
          <li>
            <input v-model="form.submitMessage" type="text" />
          </li>
        </ul>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data() {
    return {
      isSubmitted: false,
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
      this.submitSuccess();
      console.log({
        greet: this.form.submitMessage,
        name: this.form.insuredName,
        item: this.form.insuredItem,
        value: this.form.insuredValue,
        income: this.form.insuredIncome
      });
    },
    submitSuccess() {
      this.isSubmitted = true;
    }
  }
};
</script>

<style>
.primaryView,
.secondaryView {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: grid;
  min-height: 100vh;
  place-items: center;
  background: whitesmoke;
  justify-items: stretch;
  font-family: 'Avenir';
  font-weight: normal;
  font-style: normal;
  line-height: 1.4;
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
