<template>
  <div class="opntions-container">
    <ul>
      <li
        :class="`list-${checked} btn btn-outline-light`"
        v-for="pokemon in pokemons"
        :key="pokemon.id"
        @click="$emit('pokemon-selection', pokemon.id)"
      >
        {{ pokemon.name }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'VueappPokemonoptions',
  props: {
    pokemons: {
      type: Array,
      required: true,
    },
    checked: {
      type: String,
      required: true,
    },
  },

  data() {
    return {};
  },

  mounted() {
    this.checkListStyle();
    console.log('checked', this?.checked);
  },

  methods: {
    checkListStyle() {
      this.pokemons.forEach((element) => {
        console.log('...', element);
      });
    },
    checkAnswer(selectedid) {
      if (selectedid === this.pokemon.id) {
        this.showpokemon = true;
        return 'active';
      } else if (selectedid !== this.pokemon.id) {
        return 'disable';
      } else {
        return null;
      }
    },
  },
};
</script>

<style scoped>
ul {
  list-style-type: none;
  margin-right: 24px;
}
li {
  border-radius: 5px;
  cursor: pointer;
  margin-bottom: 10px;
  padding: 5px;
  max-width: 250px;
  text-transform: uppercase;
  font-weight: 700;
  font-family: 'Metal Mania', cursive;
  color: #9e0504;
  display: flex;
  justify-content: center;
  margin: auto;
  margin-bottom: 10px;
  border: none;
  background-color: azure;
  opacity: 0.9;
}
.btn-outline-light:hover {
  color: #fff;
  background-color: #2a6eb6;
  border-color: none;
  border: none;
}

li:hover {
  color: white;
}

.options-container {
  display: flex;
  justify-content: center;
  align-content: center;
}
</style>
