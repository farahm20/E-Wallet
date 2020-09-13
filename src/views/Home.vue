<template>
  <main id="home">
    <Card :card="cardRecieved" class="active" />
    <CardStack :cards="cards" @setCard="setCard" /> 

  </main>
</template>

<script>
import Card from "../components/Card"
import CardStack from "../components/CardStack"


export default {
  name: "Home",
  data: () => {
    return {
      cardRecieved: {},
      savedCards: localStorage.getItem("cards"), //recieving the stored cards from local storage
      index: "",
      cards: [] 
    };
  },
  components: {
    Card, 
    CardStack,
  },
  methods: {
    setCard(index) {
      this.index = index;
    },
    addCard() {
      this.$router.push("/AddCard");
    }
  },
  watch: {
    savedCards() {
      this.cards = JSON.parse(this.savedCards);
    }
  },
  mounted() {
    if (localStorage.getItem("cards")) {
      this.cards = JSON.parse(localStorage.getItem("cards"));
    } else {
      localStorage.setItem("cards", JSON.stringify(this.cards));
    }
  
    // Active Card
    if (localStorage.getItem("cardRecieved")) {
      this.activeCard = JSON.parse(localStorage.getItem("cardRecieved"));
    }
  
  }
  
}
</script>

<style>

#home{
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>