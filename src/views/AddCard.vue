<template>
  <section id="cardSection">
    <Card :card="card" />
    <CardForm @addCard = "addCard" @addCardInfo = "addCardInfo"/>
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
        cards: []
    };
  },
  components: {
    CardForm,
    Card,
  },
  methods: {
      addCardInfo(input) {
          this.card = input;
      },
      addCard(){
        //check if data enetered is correct. Then add from
        if(this.card.check === true) {
            this.cards = JSON.parse(localStorage.getItem("cards"));
            this.cards.push(this.card);
            localStorage.setItem("cards", JSON.stringify(this.cards));
            this.$router.push("/");
        } else {
          alert("Please enter correct data");
        }

      }
  },
};
</script>

<style>
#cardSection{
    display: flex;
    flex-direction: column;
    align-items: center;
}
button {
    color: white;
    text-align: center;
    width: 360px;
    height: 50px;
    border-radius: 8px;
    background-color: black;
}
</style>