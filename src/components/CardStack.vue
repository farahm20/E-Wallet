<template>
    <div id="cards">
      <!--Here we will show all the cards in the wallet-->
      <!--Accessing the cards Array-->
      <div 
        v-for="(card, index) in cards" 
        :key="index"
        @click="setCard(index)" 
        class="cardContainer" >
          
        <Card class="card" :card="card"/>
      </div>
    </div>
</template>


<script>
import Card from "../components/Card"

export default {
  components: {
    Card,
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


  .card {
    cursor:grab;
  }

  .cardContainer {
    overflow: hidden;
    cursor: pointer;
    height: 40px;
  }

  .cardContainer:last-child {
    height: 370px;
  }



</style>