<template>
  <div class="containerpages">
    <img
      v-if="pokemon.id"
      class="title-one"
      src="@/assets/whois.png"
      alt="..."
    />
    <img
      v-if="!pokemon.id"
      src="https://c.tenor.com/fSsxftCb8w0AAAAi/pikachu-running.gif"
      alt="pikachu"
      class="pikachuload"
    />
    <div class="subcontent" v-if="pokemon.id">
      <img src="@/assets/pokemon.png" class="title-span" />
      <img
        v-if="pokemon.id"
        class="title-interrogative"
        src="@/assets/interrogative.png"
        alt=""
      />
      <PokemonPicture
        :pokemonId="pokemon.id"
        :showpokemon="showpokemon"
      ></PokemonPicture>
      <div class="content-buttons">
        <PokemonOptions
          @pokemon-selection="checkAnswer"
          :pokemons="pokemonarr"
          :checked="showcheked"
        ></PokemonOptions>
        <span class="content-poball">
          <img
            class="pokebutonball"
            @click="restar"
            src="../assets/pokebola.png"
            alt=""
          />
          <h3 @click="restar" class="titleball">Play</h3>
        </span>
      </div>
    </div>
  </div>
</template>

<script>
import PokemonOptions from '@/components/pokemonOptions.vue';
import PokemonPicture from '@/components/pokemonPicture.vue';
import getPokemonOptions from '@/helpers/getPokemonsOptions';

export default {
  name: 'VueappPokemonpages',
  components: {
    PokemonPicture,
    PokemonOptions,
  },

  data() {
    return {
      pokemonarr: [],
      pokemon: {},
      showpokemon: false,
      showcheked: String,
    };
  },

  mounted() {
    this.mixedpokemonArray();
    this.changeBlendMode();
  },
  watch: {
    showpokemon(newshow, oldshow) {
      console.log('from', oldshow, 'to', newshow);
      if (newshow === true) {
        setTimeout(() => {
          console.log('asda');
        }, 1000);
      }
    },
  },
  methods: {
    async mixedpokemonArray() {
      this.pokemonarr = await getPokemonOptions();
      const rndInteger = Math.floor(Math.random() * 4);
      this.pokemon = this.pokemonarr[rndInteger];
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
    changeBlendMode() {
      const x = document.getElementsByClassName('main')[0];
      console.log('la x', x);

      setInterval(() => {
        x.style.backgroundBlendMode = 'hard-light';
      }, 4000);
    },
    restar() {
      this.showpokemon = false;
      this.mixedpokemonArray();
    },
  },
};
</script>

<style scoped>
.content-poball {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}
.pokebutonball {
  width: 100px;
  height: 130px;
  cursor: pointer;
}
.titleball {
  position: absolute;
  color: white;
  font-size: 25px;
  font-weight: 700;
  cursor: pointer;
  bottom: 60px;
}
.title-one {
  width: 260px;
  height: 60px;
  position: relative;
  left: 70px;
  top: 45px;
}
.title-interrogative {
  position: relative;
  transform: rotateZ(35deg);
  top: 31px;
}

.containerpages {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.title-span {
  width: 325px;
  height: 130px;
}
.subcontent {
  margin-top: 50px;
}
.content-buttons {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-content: center;
}
.pikachuload {
  width: 300px;
  height: 200px;
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  margin: auto;
}
@media (max-width: 450px) {
  .title-interrogative {
    display: none;
  }
  .title-one {
    left: 52px;
    width: 170px;
    height: 52px;
  }
  .title-span {
    width: 260px;
    height: 90px;
  }
}
</style>
