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
      this.$emit("setCard", index)
    }
  }
};
</script>

<style scoped>
    #cards{
        width: 100%;
        max-width: 1200px;
        margin: 40px auto;
        padding: 0 20px;
        box-sizing: border-box;
    }

    ul{
        display: flex;
        flex-wrap: wrap;
        list-style-type: none;
        padding: 0;
    }

    li{
        flex-grow: 1;
        flex-basis: 300px;
        text-align: center;
        padding: 30px;
        border: 1px solid #222;
        margin: 10px;
    }
</style>