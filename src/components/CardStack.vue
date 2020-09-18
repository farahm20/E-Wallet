<template>
    <div id="cards">
      <!--Here we will show all the cards in the wallet-->
      <!--Accessing the cards Array-->
      <div 
        v-for="(card, index) in cards" 
        :key="index"
        @click="setCard(index)" 
        class="cardContainer" >
          
        <Card id="theCard" :card="card"/>
      </div>
    </div>
</template>


<script>
import Card from "../components/Card"

export default {
  components: {
    Card
  },
  props: {
    cards: Array 
  },
  methods: {
    setCard(index) {
      console.log("cardstack" + index);
      this.$emit("setCard", index)
    }
  }
};
</script>

<style lang="scss" scoped>
#cards {
  height: 24rem;

  .cardContainer:last-child {
    overflow: visible;
  }

  #theCard {
    cursor: pointer;
    height: 2.5rem;
  }
}
</style>