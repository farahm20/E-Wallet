<template>
  <section>
      <button @click="active" class="set-card">Set Active</button>
  </section>
</template>

<script>
export default {
    methods: {
        active() {
            this.$emit("active");
        }
    }
};
</script>

<style>

</style>