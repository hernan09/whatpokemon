<template>
  <div class="pokemoncontainer">
    <img class="hiden-pokemon" :src="imgSrc" alt="pokemon" />
    <img
      v-if="showpokemon"
      class="jello-horizontal pokemonId"
      :src="imgSrc"
      alt="pokemon"
    />
  </div>
</template>

<script>
export default {
  name: 'VueappPokemonpicture',
  props: {
    pokemonId: {
      type: Number,
      required: true,
    },
    showpokemon: {
      type: Boolean,
      required: true,
      default: false,
    },
  },
  computed: {
    imgSrc() {
      return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokemonId}.svg`;
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
.pokemoncontainer {
  height: 250px;
  display: flex;
  justify-content: center;
}
.hiden-pokemon {
  filter: brightness(0);
}
img {
  height: 200px;
  width: 200px;
  position: absolute;
  user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  -webkit-user-drag: none;
  -webkit-user-select: none;
}
</style>
