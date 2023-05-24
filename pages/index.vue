<template>
  <div class="container">
    <section class="filter">
      <AppInput
        v-model="searchText"
        placeholder="Search for a country..."
        icon="fa-search"
      />
      <AppSelectOption :options="getRegions" v-model="selectedRegion" />
    </section>
    <section class="cards">
      <div v-for="country in getCountries" :key="country.name">
        <NuxtLink
          style="text-decoration: none; color: inherit"
          :to="'/details/' + country.name"
          ><AppCard
            :src="country.flags.svg"
            :title="country.name"
            :details="getCountryDetails(country)"
          ></AppCard
        ></NuxtLink>
      </div>
    </section>
  </div>
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
  return countries.value.reduce((acc, curr) => {
    if (acc.indexOf(curr.region) === -1) acc.push(curr.region);
    return acc;
  }, []);
});
</script>

<style lang="scss" scoped>
.container {
  padding: 40px 60px;
}
.filter {
  display: flex;
  justify-content: space-between;
}
.cards {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  grid-gap: 50px;
  margin-top: 40px;
}
</style>
