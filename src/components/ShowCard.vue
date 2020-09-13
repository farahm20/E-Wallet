<template>
  <section>
      <button @click="active" class="set-card">Set Active</button>
  </section>
</template>

<script>
export default {
    methods: {
        actuve() {
            this.$emit("active");
        }
    }
};
</script>

<style>

</style>