<template>
    <ul id="list">
        <li class="country" v-for="country in countries" :key="country.alpha3Code">
            <img class="countryFlag" :src="`https://flagpedia.net/data/flags/w1160/${country.alpha2Code.toLowerCase()}.png`" :alt="`Flag of ${country.name.common}`">
            <p class="countryName"><router-link :to="{ name: 'details', params: { alpha3Code: country.alpha3Code } }">{{ country.name.common }}</router-link></p>
        </li>
    </ul>
    <router-view />
</template>

<script>
import countries from '../../public/countries.json';

export default {
    name: 'CountriesList',
    data() {
        return {
            countries,
        }
    }
}
</script>

<style scoped>
    #list {
        padding: 80px;
        width: 40vw;
        position: relative;
        margin-left: 0;
        border: 2px darkslategray solid;
        z-index: -1;
        float: left;
    }

    .country {
        list-style: none;
        text-align: center;
        margin-top: 20px;
    }

    .countryFlag {
        width: 100px;
    }

    .countryName {
        font-weight: 500;
        padding: 10px;
    }

</style>
