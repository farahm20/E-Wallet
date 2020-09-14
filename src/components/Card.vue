<template>
  <div :class="vendorColor" id="card">
    <!--bining a list of classes-->
    <article :class="['card',vendor, chip]">
      <div class="chip">
        <img :src="require(`../assets/${chip}.svg`)" alt />
        <img :src="require(`../assets/${vendor}.svg`)" alt />
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
      let chip = "dark";
      if (!this.card.vendor) {
        return chip;
      } else if (this.card.vendor === "ninja") {
        return chip;
      } else {
        chip = "light";
        return chip;
      }
    },
    vendor() {
      
      if (!this.card.vendor) {
        return this.displayVendor;
      } else {
        return this.card.vendor;
      }
    },
    vendorColor() {
      let className = "";

      if (this.vendor === "ninja") {
        className = "ninja";
      }
      return className;
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
    color: #fffc
  }
  &.bitcoin {
    background-color: #FFAE34;
    color: #444
  } 
  &.blockchain {
    background-color: #8B58F9;
    color: #fffc
  }
  &.evil {
    background-color: #F33355;
    color: #fffc
  }
}

.card {
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

p {
  font-size: 20px;
}

img {
  transform: scale(0.8);
}
</style>