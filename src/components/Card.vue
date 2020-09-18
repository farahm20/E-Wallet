<template>
  <div :class="vendor" id="card">
    <!--bining a list of classes-->
    <article id="chipVendorArea" :class="['card', chip]">
      <div class="chip">
        <img :src="require(`../assets/${chip}.svg`)" alt />
        <img :src="require(`../assets/${vendor}.svg`)" alt />
      </div>
    </article>

    <article id="number">
      <h2>{{ card.number }}</h2>
    </article>
    
    <div class="secondHalf">
        <article id="name">
          <p>CARD HOLDER </p>
          <h2>{{ card.name }}</h2>
        </article>

        <article id="validity">
          <p>VALID THRU </p>
          <h2>{{ card.date }}</h2>
        </article>
    </div>
  </div>
</template>

<script>
export default {
  name: "BankCard",
  props: {
    card: Object,
  },
  data: () => {
    return {
      displayVendor: "ninja",
      displayNumber: "xxxx xxxx xxxx xxxx",
      displayName: "Firstname Lastname",
      displayDate: "mm/yy",
    };
  },
  methods: {},
  computed: {
    chip() {
      let chip = "light";
      if (!this.card.vendor) {
        return chip;
      } else if (this.card.vendor === "ninja") {
        chip = "light";
      } else {
        chip = "dark";
      }
      return chip;
    },
    vendor() {
      if (!this.card.vendor) {
        return this.displayVendor;
      } else {
        return this.card.vendor;
      }
    },
    number() {
      if (!this.card.number) {
        return this.displayNumber;
      } else {
        let num = this.card.number;
        num = num.match(/.{1,4}/g);
        return num.join(" ");
      }
    },
    name() {
      if (!this.card.name) {
        return this.displayName;
      } else {
        return this.card.name;
      }
    },
    date() {
      if (!this.card.date) {
        return this.displayDate;
      } else {
        return this.card.date;
      }
    },
  },
};
</script>


<style lang="scss" scoped>
div {
  &.ninja {
    background-color: #222222;
    color: #fffc;
  }
  &.bitcoin {
    background-color: #ffae34;
    color: #444;
  }
  &.blockchain {
    background-color: #8b58f9;
    color: #fffc;
  }
  &.evil {
    background-color: #f33355;
    color: #fffc;
  }
}

#card {
  width: 24rem;
  height: 15rem;

  display: grid;
  grid-template-areas:
    "chip chip chip chip"
    "number number number number"
    "name name name validity";
  grid-template-rows: 70px 45px 50px;
  row-gap: 10px;

  align-content: flex-start;
  border-radius: 10px;
  box-shadow: 2px;
  font-family: monospace;

  .label {
    font-size: 0.8rem;
    margin-right: 20px;
    margin-left: 10px;
  }

  #number {
    grid-area: number;
    font-size: 1.5rem;
    width: 23rem;
    margin-left: 10px;
    margin-top: 10px;
  }

  #name {
    grid-area: name;
    width: 16rem;
    margin-left: 10px;
  }

  #validity {
    grid-area: validity;
    margin-right: 4px;
  }

  #chipVendorArea {
    grid-area: chip;
    /* display: flex; */
    margin-right: 20px;
    margin-left: 10px;
  }

  .chip {
  //  grid-area: chip;
    display: flex;
    justify-content: space-between;

    .vendor {
      margin-top: 2.5rem;
      margin-right: 1rem;
    }

    .dark {
      color: black;
      text-shadow: -0.5px 0.5px 0px #3a3a3a;
    }
    .light {
      color: white;
      text-shadow: 0.5px 0.5px 0px #868686, -0.5px -0.5px 0px #868686;
    }
  }
}
.secondHalf {
    display: flex;
    margin: 0;
    padding: 0;
    flex-direction: column;
    justify-content: space-between;
    flex-wrap: wrap;
    margin-top: 30px;
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
//  padding: 30px;
  border: 1px solid #222;
//  margin: 10px;
}

p {
  font-size: 16px;
  padding: 0;
  margin: 0px;
}

h2 {
  margin: 0;
  font-family: "Source Sans Pro";
}

img {
  transform: scale(0.8);
}
</style>