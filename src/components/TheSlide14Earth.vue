<template>
  <div>
    <section class="slide">
      <div class="slide__caption">
        <h2>Ziemia</h2>
      </div>
      <div class="slide__image">
        <img
          src="../assets/599px-The_Earth_seen_from_Apollo_17.jpg"
          alt="Ziemia"
        />
      </div>
      <div class="slide__tile-text">
        <p>
          Ziemia - trzecia w kolejności planeta od Słońca. Liczy około 4,5 mld
          lat. Posiada gęstą atmosferę składającą się w 78% z azotu, 21% z tlenu
          i innych gazów. Jest chroniona przed wiatrem słonecznym poprzez pole
          magnetyczne, wytwarzane przez płynne jądro.
          <br />
          <br />
          Masa: 5,97 × 10²⁴ kg
          <br />
          <br />
          Promień: 6371 km
          <br />
          <br />
          Średnia temperatura: 15° C
        </p>
      </div>
      <div class="slide__caption-aside">
        <h3>Zorza polarna</h3>
      </div>
      <div class="slide__image-aside">
        <img src="../assets/1280px-Polarlicht_2.jpg" alt="Zorza polarna" />
      </div>
      <div v-if="!loaded" class="slide__button">
        <button @click="engage">Więcej zdjęć</button>
      </div>
    </section>
    <div v-if="results && loaded">
      <TheSlide11Fetch
        v-for="(item, index) in results"
        :item="item"
        :index="index + 1"
        :key="item.data[0].nasa_id"
        :id="`ear-pic${index}`"
      />
    </div>
    <TheButton @click="pushImages" v-if="loaded" />
  </div>
</template>

<script>
import TheSlide11Fetch from "@/components/TheSlide11Fetch.vue";
import TheButton from "@/components/TheButton.vue";

export default {
  name: "TheSlide14Earth",
  components: {
    TheSlide11Fetch,
    TheButton,
  },
  data() {
    return {
      results: [],
      superResults: [],
      loaded: false,
      currentPic: 9,
    };
  },
  methods: {
    engage() {
      this.loaded = true;
      this.fetchImages();
    },
    async fetchImages() {
      const API = "https://images-api.nasa.gov/search?q=Earth";

      let response = await fetch(`${API}&media_type=image`);
      let jsonResponse = await response.json();
      this.superResults = jsonResponse.collection.items;

      this.pushImages(this.currentPic, this.superResults);
    },
    async pushImages() {
      let positionY = window.scrollY;
      this.results = this.superResults.slice(0, this.currentPic);
      if (this.currentPic == 9) {
        await this.$nextTick();
        document.querySelector("#ear-pic0").scrollIntoView({
          behavior: "smooth",
        });
      } else {
        await this.$nextTick();
        window.scroll(window.scrollX, positionY);
        document
          .querySelector(`#ear-pic${this.currentPic - 10}`)
          .scrollIntoView({
            behavior: "smooth",
          });
      }
      this.currentPic += 10;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import "../scss/_variables.scss";
@import "../scss/_extensions.scss";

.slide {
  @extend %slide-settings;
  grid-template-rows: repeat(21, 16.6666vw);
  grid-template-areas:
    ".    .    .    cap  cap  cap   "
    "img  img  img  img  img  img   "
    "img  img  img  img  img  img   "
    "img  img  img  img  img  img   "
    "img  img  img  img  img  img   "
    "text text text text text .  "
    "text text text text text .  "
    "text text text text text .  "
    "text text text text text .     "
    "text text text text text .     "
    "text text text text text .     "
    "text text text text text .     "
    ".    .    .    .    .    .     "
    "capa  capa  capa    .    .    .     "
    "imga  imga  imga  imga  imga  imga   "
    "imga  imga  imga  imga  imga  imga   "
    "imga  imga  imga  imga  imga  imga   "
    "imga  imga  imga  imga  imga  imga   "
    ".    .    .    .    .    .     "
    ".    but  but  but  but  .     "
    ".    .    .    .    .    .     ";

  @media screen and (min-width: 700px) {
    grid-template-rows: repeat(20, 6.5vw);
    grid-template-areas:
      ".    .    .   .   .    .    cap  cap  cap cap "
      "img  img  img img img  img  img  img  img img "
      "img  img  img img img  img  img  img  img img "
      "img  img  img img img  img  img  img  img img "
      "img  img  img img img  img  img  img  img img "
      "img  img  img img img  img  img  img  img img "
      "text text text text text text text text text text"
      "text text text text text text text text text text"
      "text text text text text text text text text text"
      "text text text text text text text text text text"
      ".    .    .    .    .    .    .    .    .    .   "
      "capa capa capa capa .    .    .    .    .    .   "
      "imga  imga  imga  imga imga   imga imga  imga  imga  imga "
      "imga  imga  imga  imga imga   imga imga  imga  imga  imga "
      "imga  imga  imga  imga imga   imga imga  imga  imga  imga "
      "imga  imga  imga  imga imga   imga imga  imga  imga  imga "
      "imga  imga  imga  imga imga   imga imga  imga  imga  imga "
      ".    .    .    .    .    .    .    .    .    .   "
      ".    .    .    but  but  but  but  .    .    .   "
      ".    .    .    .    .    .    .    .    .    .   ";
  }

  &__caption {
    grid-area: cap;
    @extend %tile-white;
    /* @extend %tile-purple; */
  }

  &__image {
    grid-area: img;
    display: flex;
    justify-content: center;
    align-items: center;

    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }

  &__tile-text {
    grid-area: text;
    @extend %tile-gray-text;
  }

  &__caption-aside {
    grid-area: capa;
    @extend %tile-purple;

    @media screen and (min-width: 700px) {
      font-size: 2vw;
    }
  }

  &__image-aside {
    grid-area: imga;
    display: flex;
    justify-content: center;
    align-items: center;

    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }

  &__button {
    grid-area: but;

    button {
      width: 100%;
      height: 100%;
      @extend %button;
    }
  }
}
</style>
