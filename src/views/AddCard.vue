<template>
  <section id="cardSection">
    <Card :card="card" />
    <CardForm @addCard="addCard" @addCardInfo="addCardInfo" />

    <div class="button">
      <button @click="addCard">Add Card</button>
    </div>
  </section>
</template>

<script>
import CardForm from "../components/CardForm.vue";
import Card from "../components/Card.vue";

export default {
  data() {
    return {
      card: {},
      cards: [],
    };
  },
  components: {
    CardForm,
    Card,
  },
  methods: {
    addCardInfo(input) {
      return this.card = input;
    },
    addCard() {
      console.log('oh, it entered the function');
      //check if data enetered is correct. Then add from
      if (this.card.check === true) {
        console.log('Localstorage: ', localStorage.getItem("cards"));
        if (localStorage.getItem("cards") !== 'undefined') {
          
          this.cards = JSON.parse(localStorage.getItem("cards"));

        //console.log(this.card); 
          this.cards.push(this.card);
          localStorage.setItem("cards", JSON.stringify(this.cards));
        } else {
          this.cards.push(this.card);
          localStorage.setItem("cards", JSON.stringify(this.cards));
          console.log('here then?'); 
        }
        this.$router.push("/");
        //
      } else {
        alert("Please enter correct data");
      }
    },
  },
};
</script>

<style lang="scss" scoped>
#cardSection {
  display: flex;
  flex-direction: column;
  align-items: center;

  button {
    color: white;
    text-align: center;
    width: 370px;
    height: 50px;
    border-radius: 8px;
    background-color: black;
  }
}
</style>