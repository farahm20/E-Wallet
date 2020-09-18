<template>
  <section class="editButtons">
      <button @click="active" class="set-card">Active</button>
      <button @click="remove" class="set-card">Delete</button>
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
    width: 40px;
    height: 40px;
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    justify-content: space-around;
}
</style>