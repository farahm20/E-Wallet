<template>
  <div class="card">
      <!--bining a list of classes-->
      <article :class="['card']">
        <div class="chip">
          <img :src="require(`../assets/${chip}.svg`)" alt="">
        <img :src="require(`../assets/${chip}.svg`)" alt />
        </div>
      </article>

    <article id="number"> 
      <p>CARDHOLDER NUMBER</p>
      <h2>{{ card.number }}</h2>
       
    </article>

    <article id="name">
      <p>CARDHOLDER NAME</p>
      <h2>{{ card.name }}</h2>
    </article>

    <article id="validity">
      <p>VALID THROUGH</p>
      <h2>{{ card.date }}</h2>
    </article>

  </div>
</template>

<script>
export default {
  name: "BankCard",
  props: {
    card: Object
  },
  methods: {
    number() {
      console.log("Displaying card number: " + this.cardNumber)
      return this.cardNumber;
    },
    holder() {
      return this.card.name;
    }
  },
  computed: {
    chip() {
      let chip = "dark";
      if(!this.card.vendor){
        return chip;
      } else if (this.card.vendor === "ninja") {
        return chip;
      } else {
        chip = "light";
        return chip;
      }
    },
    vendor() {
      console.log(this.card.vendor.JSON.stingify)
      return this.card.vendor;
    }
  },
  data: () => {
    return {
      cardImg: "ninja",
      cardNumber: "XXXX XXXX XXXX XXXX",
      cardName: "Firstname Lastname",
      cardValidity: "MM/YY" 
    };
  },
};
</script>


<style scoped>
.card{
  background-color: red;
  border-radius: 6px;
  width: 370px;
}
#cards {
  width: 100%;
  max-width: 1200px;
  margin: 40px auto;
  padding: 0 20px;
  box-sizing: border-box;
}

ul {
  display: flex;
  flex-wrap: wrap;
  list-style-type: none;
  padding: 0;
}

li {
  flex-grow: 1;
  flex-basis: 300px;
  text-align: center;
  padding: 30px;
  border: 1px solid #222;
  margin: 10px;
}

p{
  font-size: 20px;
}

img{
  transform: scale(0.8);
}
</style>