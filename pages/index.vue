<template>
  <section class="filter">
    <AppInput
      v-model="searchText"
      placeholder="Search for a country..."
      icon="fa-solid fa-search"
    />
    <AppSelectOption :options="getRegions" v-model="selectedRegion" />
  </section>
  <section class="cards">
    <div
      class="cards__item"
      v-for="country in getCountries"
      :key="country.alpha3Code"
    >
      <NuxtLink
        style="text-decoration: none; color: inherit"
        :to="'/details/' + country.alpha3Code"
        ><AppCard
          :src="country.flag"
          :title="country.name"
          :details="getCountryDetails(country)"
        ></AppCard
      ></NuxtLink>
    </div>
  </section>
</template>

<script setup>
let searchText = ref("");
let selectedRegion = ref("");

const queryString = computed(() =>
  selectedRegion.value ? `region/${selectedRegion.value}` : "all"
);

const { data: countries } = await useLazyAsyncData(
  "countries",
  () => $fetch(`https://restcountries.com/v2/${queryString.value}`),
  {
    watch: [queryString.value],
  }
);

const getCountries = computed(() =>
  countries.value?.filter(
    (country) =>
      country.name.toLowerCase().includes(searchText.value.toLowerCase()) &&
      country.region.includes(selectedRegion.value)
  )
);

const getCountryDetails = computed(() => {
  return ({ region, population, capital }) => ({
    Region: region?.charAt(0).toUpperCase() + region?.slice(1),
    Population: population,
    Capital: capital?.charAt(0).toUpperCase() + capital?.slice(1),
  });
});

const getRegions = computed(() => {
  return countries.value?.reduce((acc, curr) => {
    if (acc.indexOf(curr.region) === -1) acc.push(curr.region);
    return acc;
  }, []);
});
</script>

<style lang="scss" scoped>
.filter {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  grid-gap: 20px;
}
.cards {
  margin-top: 50px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
  grid-gap: 50px;
  &__item {
    flex-grow: 1;
  }
}
</style>
