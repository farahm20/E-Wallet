<template>
  <main id="home">
    <Card :card="cardRecieved" class="active" />
    <section class="cardEdit">
      <CardStack :cards="cards" @setCard="setCard" />
      <EditCard v-if="editButtonIs" @active="active" @remove="remove" />
    </section>
  </main>
</template>

<script>
import Card from "../components/Card";
import CardStack from "../components/CardStack";
import EditCard from "../components/ShowCard";

export default {
  name: "Home",
  data: () => {
    return {
      savedCards: localStorage.getItem("cards"), //recieving the stored cards from local storage
      index: "",
      cards: [],
      cardRecieved: {},
      editButtonIs: false,
    };
  },
  components: {
    Card,
    CardStack,
    EditCard,
  },
  methods: {
    addCard() {
      this.$router.push("/AddCard");
    },
    //going to AddCard page
    setCard(index) {
      this.index = index;
      this.editButtonIs = true;
    },
    
    //setting card as active or deleting card from CardStack
    //set card as active. bring to top. store in local storage.
    active() {
      const card = this.cards[this.index];
      localStorage.setItem("cardRecieved", JSON.stringify(card));
      this.cardRecieved = card;
      this.editButtonIs = false;
    },
    //remove card from stack and localstorage
    remove() {
      this.cards.splice[(this.index, 1)];
      localStorage.setItem("cards", JSON.stringify(this.card));
      this.cardRecieved = {};
      this.editButtonIs = false;
    },
  },
  watch: {
    savedCards() {
      this.cards = JSON.parse(this.savedCards);
    },
  },
  mounted() {
    if (localStorage.getItem("cards")) {
      this.cards = JSON.parse(localStorage.getItem("cards"));
    } else {
      localStorage.setItem("cards", JSON.stringify(this.cards));
    }

    // Active Card
    if (localStorage.getItem("cardRecieved")) {
      this.cardRecieved = JSON.parse(localStorage.getItem("cardRecieved"));
    }
  },
};
</script>

<style lang="scss" scoped>
#home {
  display: flex;
  flex-direction: column;
  align-items: center;

  .cardEdit {
    display: flex;
    flex-direction: column;
    margin-top: 80px;;
  }

  .active {
    height: 240px;
  }
}
</style>
