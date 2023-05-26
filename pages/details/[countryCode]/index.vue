<template>
  <NuxtLink to="/" style="text-decoration: none; color: inherit">
    <AppButton title="Back" icon="fa-long-arrow-left" />
  </NuxtLink>
  <section class="details">
    <img class="details__img" :src="country?.flag" />
    <div class="details__text">
      <p class="details__title">{{ country.name }}</p>
      <div class="details__statistics">
        <p>
          <span class="details__key">Native Name: </span>
          {{ country.nativeName }}
        </p>
        <p>
          <span class="details__key">Population: </span>
          {{ country.population }}
        </p>
        <p><span class="details__key">Region: </span>{{ country.region }}</p>
        <p>
          <span class="details__key">Sub Region: </span>{{ country.subregion }}
        </p>
        <p><span class="details__key">Capital: </span>{{ country.capital }}</p>
        <p>
          <span class="details__key">Top Level Domain: </span>
          {{ country.topLevelDomain.join(", ") }}
        </p>
        <p>
          <span class="details__key">Currencies: </span>
          {{ country.currencies.map((language) => language.name).join(", ") }}
        </p>
        <p>
          <span class="details__key">Languages: </span>

          {{ country.languages.map((language) => language.name).join(", ") }}
        </p>
      </div>
      <div class="borders" v-if="country.borders">
        <span class="details__key"> Border Countries: </span>
        <div
          class="borders__item"
          v-for="border in country.borders"
          :key="border"
        >
          <AppTag :title="border" :to="'/details/' + border"> </AppTag>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const { countryCode } = useRoute().params;
const { data: country } = await useFetch(
  `https://restcountries.com/v2/alpha/${countryCode}`
);
</script>

<style lang="scss" scoped>
.details {
  display: flex;
  margin-top: 50px;
  justify-content: space-between;
  flex-wrap: wrap;
  &__img {
    width: 400px;
    height: 300px;
  }
  &__text {
    font-size: 0.875rem;
  }
  &__title {
    font-weight: 800;
    font-size: 1.5rem;
  }
  &__statistics {
    display: grid;
    grid-template-rows: 1fr 1fr 1fr 1fr 1fr;
    grid-auto-flow: column;
    grid-column-gap: 20px;
  }
  &__key {
    font-weight: 800;
  }
  .borders {
    display: flex;
    flex-wrap: wrap;
    grid-gap: 10px;
    &__item {
      margin-left: 10px;
    }
  }
}
</style>
