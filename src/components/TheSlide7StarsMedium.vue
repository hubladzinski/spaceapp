<template>
  <section class="slide">
    <div class="slide__star-hero">
      <h1>Gwiazdy średniej masy</h1>
    </div>
    <div class="slide__caption">
      <h2>Słońce</h2>
    </div>
    <div class="slide__image">
      <img
        src="../assets/1024px-Solar_prominence_from_STEREO_spacecraft_September_29,_2008.jpg"
        alt="Słońce"
      />
    </div>
    <div class="slide__tile-text">
      <p>
        Gwiazda średniej masy w granicach od 0.5 do 10 mas Słońca. Obiekty tego
        typu są w stanie “spalać” cięższe pierwiastki uzyskując z nich energię,
        w trakcie zamiany “paliwa” znacznie zwiększają swoją średnicę, nawet
        kilkusetkrotnie.
      </p>
    </div>
    <div class="slide__tile-text2">
      <p>
        Pod koniec życia, gwiazda taka odrzuca swoją zewnętrzną otoczkę, tworząc
        mgławicę planetarną. Po gwieździe pozostaje jedynie biały karzeł o
        średnicy zaledwie kilku tysięcy kilometrów. Cały proces zajmuje znacznie
        krócej niż w przypadku gwiazd małomasywnych, w zależności od masy od
        kilkuset milionów do kilku miliardów lat.
      </p>
    </div>
    <aside class="slide__tile-side">
      <p>
        Temperatura we wnętrzu Słońca - które jest gwiazdą o średniej masie,
        wynosi około 10 milionów stopni Celcjusza.
      </p>
    </aside>
    <div class="slide__tile-fill"></div>
    <div class="slide__tile-fill2"></div>
  </section>
</template>

<script>
export default {
  name: "TheSlide7StarsMedium",
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import "../scss/_variables.scss";
@import "../scss/_extensions.scss";

.slide {
  @extend %slide-settings;
  grid-template-rows: repeat(24, 16.6666vw);
  grid-template-areas:
    "hero hero hero hero hero .   "
    "hero hero hero hero hero .   "
    "hero hero hero hero hero .   "
    ".    .    .    .    .    .   "
    ".    .    .    cap  cap  cap "
    "img  img  img  img  img  img"
    "img  img  img  img  img  img"
    "img  img  img  img  img  img"
    "img  img  img  img  img  img"
    ".    text text text text text"
    ".    text text text text text"
    ".    text text text text text"
    ".    text text text text text"
    ".     .     .     .     .     .  "
    "text2 text2 text2 text2 text2 ."
    "text2 text2 text2 text2 text2 ."
    "text2 text2 text2 text2 text2 ."
    "text2 text2 text2 text2 text2 ."
    "text2 text2 text2 text2 text2 ."
    "text2 text2 text2 text2 text2 ."
    ".     .     .     .     .     .  "
    ". aside aside aside  aside aside  "
    ". aside aside aside aside aside  "
    ".     .     .     .     .     .  ";

  @media screen and (min-width: 700px) {
    grid-template-rows: repeat(13, 6.5vw);
    grid-template-areas:
      "hero hero hero hero hero . .   .   .   .         "
      "hero hero hero hero hero . cap cap cap cap       "
      "fil  fil  .    .    img  img  img img   img  img "
      "fil  fil  .    .    img  img  img img   img  img "
      ".    .    fil2 fil2 img  img  img img   img  img "
      ".    .    fil2 fil2 img  img  img img   img  img "
      "text text text text text text text text text text"
      "text text text text text text text text text text"
      "text2 text2 text2 text2 text2 text2 text2 text2 text2 text2"
      "text2 text2 text2 text2 text2 text2 text2 text2 text2 text2"
      "aside aside aside aside  aside aside .     .     .     .    "
      "aside aside aside aside  aside aside     .    .     .     .    "
      ".     .     .     .     .     .   . . . .";
  }

  &__star-hero {
    grid-area: hero;
    /* @extend %tile-gray-header; */
    @extend %tile-white-header;
    /*  @extend %tile-white; */
    /* @extend %tile-gray; */
  }

  &__caption {
    grid-area: cap;
    /* @extend %tile-white; */
    @extend %tile-purple;
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

  &__tile-text2 {
    grid-area: text2;
    @extend %tile-gray-text;
  }

  &__tile-side {
    grid-area: aside;
    @extend %tile-purple-text;
  }

  &__tile-fill {
    grid-area: fil;
    @extend %tile-purple;
  }

  &__tile-fill2 {
    grid-area: fil2;
    @extend %tile-purple;
  }
}
</style>
