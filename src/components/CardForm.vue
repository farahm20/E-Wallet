<template>
  <form class="cardform" @input="addCardInfo">
    <div class="form">
      <label for="cardNumber">
        Card Number
        <span v-if="checkInput.number" class="error">Invalid. Enter correct format.</span>
      </label>
      <input
        type="text"
        id="cardNumber"
        v-model="number"
        maxlength="16"
        placeholder="XXXX XXXX XXXX XXXX"
      />
    </div>

    <div class="form">
      <label for="cardName">
        Cardholder Name
        <span v-if="checkInput.name" class="error">Invalid. Enter correct format.</span>
      </label>
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
        <label for="date">
          Valid thru
          <span v-if="checkInput.date" class="error">Invalid. Enter correct format.</span>
        </label>
        <input type="text" id="date" placeholder="MM/YY" v-model="date" maxlength="5" />
      </div>

      <div class="form ccv">
        <label for="ccv">
          CCV
          <span v-if="checkInput.ccv" class="error">Invalid. Enter correct format.</span>
        </label>
        <input type="text" id="ccv" v-model="ccv" maxlength="3" />
      </div>
    </div>
    <div class="form">
      <label for="vendor">
        Vendor
        <span v-if="checkInput.vendor" class="error">Cannot be left empty.</span>
      </label>
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
  components: {},
  data: () => {
    return {
      number: "",
      name: "",
      date: "",
      ccv: "",
      vendor: "",
      checkInput: {
        number: false,
        name: false,
        date: false,
        ccv: false,
        vendor: false,
      },
    };
  },
  watch: {
    //Validatimg all the inputs
    number() {
      //Input should only contain numbers and length cannot be less than 16
      if (this.checkNumber(this.number) === true || this.number.length < 16) {
        this.checkInput.number = false;
      } else {
        this.checkInput.number = true;
      }
      //console.log("CheckInput number: " + this.checkInput.number);
    },
    name() {
      //Name should only contain letters and must be two names
      if (this.checkName(this.name) === false) {
        this.checkInput.name = true;
      } else {
        this.checkInput.name = false;
      }
     // console.log("CheckInput name: " + this.checkInput.name);
    },
    date() {
      //date format must be mm/yy
      if (this.checkDate(this.date) === false) {
        this.checkInput.date = true;
      } else {
        this.checkInput.date = false;
      }
      //console.log("CheckInput date: " + this.checkInput.date);
    },
    cvc() {
      //Must contain only 3 numbers
      if (this.checkCvc(this.cvc) === false) {
        this.checkInput.cvc = true;
      } else {
        this.checkInput.cvc = false;
      }
      //console.log("CheckInput ccv: " + this.checkInput.ccv);
    },
    vendor() {
      //vendor must be selected
      if (this.vendor === "") {
        this.checkInput.vendor = true;
      } else {
        this.checkInput.vendor = false;
      }
    },
  },
  computed: {
  
  },
  methods: {
    addCardInfo() {
      const input = {
        number: this.number,
        name: this.name,
        date: this.date,
        ccv: this.cvc,
        vendor: this.vendor,
        //Card will only ne submitted if check is true
        check: false
      };
      //checking if all checkInput keys are false
      const checkAllKeys = Object.keys(this.checkInput).every(
        (key) => !this.checkInput[key]
      );
      if (checkAllKeys === true) {
        // If true, check if any input: {key} is empty
        const emptyKey = Object.keys(input).some((key) => input[key] === "");
        console.log(emptyKey);
        if (emptyKey === false) {
          input.check = true;
        }
      }
      //emitting to AddCard
      this.$emit("addCardInfo", input);
    },
    //Checking all the input
    checkNumber(number) {
      const pattern = /^[0-9]{16}/;
      return pattern.test(number);
    },
    checkName(name) {
      const pattern = /^[a-zA-Z]+ [a-zA-Z]+$/;
      return pattern.test(name);
    },
    checkDate(date) {
      const pattern = /^(0[1-9]|1[012])\/\d{2}$/;
      return pattern.test(date);
    },
    checkCvc(cvc) {
      const pattern = /\d{3}/;
      return pattern.test(cvc);
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
  font-size: 1rem;
  margin-top: 4px;
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

 .span {
    font-size: 0.8rem;
    font-weight: 600;
    margin-left: 0.5rem;
  }
</style>
