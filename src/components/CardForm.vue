<template>
  <form class="cardform" @input="addCardInfo">
    <div class="form">
      <label for="cardNumber">Card Number</label>
      <input 
      type="text" 
      id="cardNumber" 
      v-model="number" 
      maxlength="16" 
      placeholder="XXXX XXXX XXXX XXXX"
      />
    </div>

    <div class="form">
      <label for="cardName">Cardholder Name</label>
      <input
        type="text"
        id="cardName"
        placeholder="FIRSTNAME LASTNAME"
        v-model="name"
        maxlength="30"
      />
    </div>

    <div class="formHalf">
      <div class="form valid">
        <label for="date">Valid thru</label>
        <input
          type="text"
          id="date"
          placeholder="MM/YY"
          v-model="date"
          maxlength="5"
        />
      </div>

      <div class="form ccv">
        <label for="ccv">CCV</label>
        <input type="text" 
        id="ccv" 
        v-model="ccv" 
        maxlength="3"  
        />
      </div>
    </div>
    <div class="form">
      <label for="vendor">VENDOR</label>
      <select v-model="vendor" name="vendor" id="vendor">
      <option style="display: none">Select</option>
      <option value="bitcoin">Bitcoin Inc</option>
      <option value="ninja">Ninja Bank</option>
      <option value="blockchain">Block Chain Inc</option>
      <option value="evil">Evil Corp</option>
      </select>
    </div>
  </form>
</template>

<script>
export default {
  components: {
  },
  data: () => {
    return {
        number: "",
        name: "",
        date: "",
        ccv: "",
        vendor: "",
        valid: false,
    };
  },

  methods: {
    addCardInfo() {
      const input = {
        number: this.number,
        name: this.name,
        date: this.date,
        ccv: this.cvc,
        vendor: this.vendor,
        valid: false,
      };
   //emitting to AddCard
    console.log("in cardform " + input.vendor)
    this.$emit("addCardInfo", input)
    },
  },
};
</script>

<style scoped>
.cardForm {
  display: flex;
  flex-direction: column;
  align-content: center;
}

.form {
  display: flex;
  flex-direction: column;
  align-content: center;
}

.form label {
  align-self: flex-start;
  font-size: 0.7rem;
}

.form input {
  font-family: "PT Mono";
  font-size: 16px;
  width: 350px;
  height: 30px;
  border-radius: 6px;
  border: 1px solid rgba(0, 0, 0, 0.8);
  margin: 8px 0px;
  padding: 4px;
}

.form input:focus {
  outline: none;
}

.form input::placeholder {
  color: grey;
  font-family: "PT Mono";
  font-size: 16px;
  font-weight: bold;
}

.form select {
  width: 362px;
  height: 40px;
  border-radius: 6px;
  border: 1px solid rgba(0, 0, 0, 0.4);
  margin: 8px 0px 15px 1px;
}

.form option {
  font-family: "PT Mono";
  font-size: 16px;
  text-align: center;
}

.formHalf input {
  width: 165px;
  margin: 6px 10px 0px 0px;
}

.formHalf {
  display: flex;
  justify-content: start;
}

</style>
