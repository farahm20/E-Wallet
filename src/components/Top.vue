<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>

<script>
export default {

  data() {
    return {
      title: "E-WALLET",
    };
  },
};
</script>

<style>
header {
  background: #e0e0e0;
  padding: 10px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
}

h1 {
  color: #222;
  text-align: center;
}



</style>