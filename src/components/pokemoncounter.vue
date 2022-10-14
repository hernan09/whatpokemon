<template>
  <div class="counter-content">
    <span class="counter">{{ counter }}</span>
  </div>
</template>

<script>
export default {
  name: 'PokeappPokemoncounter',
  props: {
    counter: {
      required: true,
    },
  },

  data() {
    return {};
  },

  mounted() {},

  methods: {},
};
</script>

<style scoped>
.counter-content {
  font-weight: 700;
  font-size: 20px;
  position: absolute;
  left: 15px;
  border: 2px solid white;
  color: white;
  background-color: rgb(251 4 3);
  width: 33px;
  border-radius: 16px;
  text-align: center;
  top: 57px;
}
</style>
