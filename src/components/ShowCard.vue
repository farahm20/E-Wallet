<template>
  <section class="editButtons">
      <button @click="active" class="activeCard"><i class="fas fa-check-circle"></i></button>
      <button @click="remove" class="deleteCard"><i class="fas fa-trash-alt icon trash-icon"></i></button>
  </section>
</template>

<script>
export default {
    methods: {
        active() {
            this.$emit("active");
        }, 
        remove() {
           this.$emit("remove");
        }
    }
};
</script>

<style lang="scss" scoped>
.editButtons {
    position: absolute;
    display: flex;
    flex-wrap: nowrap;
    flex-direction: row;
    align-items: flex-start;
    justify-content: space-between;
}

.activeCard {
    color: green;
}

.deleteCard {
    color: red;
}
</style>