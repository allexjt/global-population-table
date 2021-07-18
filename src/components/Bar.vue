<template>
<div class="barContainer" v-if="checkPopulationValid(this.country)">
    <h3 class="countryTag tooltip">{{ country.Country_Code }}
        <span class="tooltiptext">{{ country.Country }} <br> Population: {{ country["Year_" + year].toLocaleString() }} </span>
    </h3>
    <div class="bar" :style="barStyles"></div>
    <p class="populationText">{{ (country["Year_" + year]/1000000).toFixed(3) }}M</p>
</div>
    
</template>

<script>
export default {
    name: 'Bar',
    props: {
        country: Object,
        year: Number,
    },
    computed: {
        barStyles() {
            return {
                width: `${Math.log10(this.country["Year_" + this.year])*34}px`,
            };
        }
    },
    methods: {
        checkPopulationValid(country) {
        /*Checking if the country population data is valid for display*/
        try {
            if (country["Year_" + this.year] > 0) {
                return true;
            };
            return false;
        } catch (error) {
            return false;
        }
    }
    }
}

</script>

<style>
    .countryTag {
        margin-left: 15px;
        margin-right: 10px;
        min-width: 45px;
    }
    .barContainer {
        width: 100%;
        display: flex;
        align-items: stretch;
    }
    .bar {
        height: 50px;
        background-color: steelblue;
        margin-right: 10px;
        margin-top: 5px;
        text-align: left;
        border-left: 2px solid black;
    }
    .bar p {
        width: 50%;
        padding-left: 5px;
        color:white;
    } 
    
    .tooltip {
    position: relative;
    display: inline-block;
    border-bottom: 1px dotted steelblue;
    }

    .tooltip .tooltiptext {
    visibility: hidden;
    min-width: 120px;
    background-color: black;
    color: #fff;
    text-align: center;
    padding: 5px 0;
    border-radius: 6px;
    position: absolute;
    z-index: 1;
    top: -30px;
    left: 110%; 
    }

    .tooltip:hover .tooltiptext {
    visibility: visible;
    }

    .populationText {
        padding-right: 10px;
        padding-top: 5px;
    }
</style>