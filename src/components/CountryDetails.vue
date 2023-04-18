<template>
    <router-view>
        <div>
            <img :src="`https://flagpedia.net/data/flags/w1160/${country.alpha2Code.toLowerCase()}.png`">
            <h2>{{ country.name.common }}</h2>
            <table>
            <tr>
                <td>Capital:</td>
                <td>{{ country.capital }}</td>
            </tr>
            <tr>
                <td>Area:</td>
                <td>{{ country.area }} km2</td>
            </tr>
            <tr>
                    <td>Borders:</td>
                    <td>
                        <router-link :to="`/list/${border}`" v-for="border in country.borders">
                            {{ border }} <br>
                        </router-link>
                    </td>
            </tr>
            </table>
        </div>
    </router-view>        
</template>

<script>
import countriesData from '../../public/countries.json';

export default {
    name: 'CountryDetails',
    computed: {
        country() {
            const alpha3Code = this.$route.params.alpha3Code;
            return countriesData.find((c)=> c.alpha3Code === alpha3Code);
        },
        borderCountries() {
            const borderCountryCodes = this.country.borders;
            const borderCountries = countries.filter((c) => borderCountryCodes.includes(c.alpha3Code));
            return borderCountries.map((c) => c.name.common).join(", ");
        }
    },
};
</script>