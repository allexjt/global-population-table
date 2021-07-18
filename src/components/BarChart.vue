<template>
<div class="barChart">
    <h2>{{title}}</h2>
        <div class="countries">
            <Bar v-for="country in populationData" v-bind:key="country.Country_Code" :country="country" :year="year" />
        </div>
</div>
    
</template>

<script>
import Bar from './Bar'

export default {
    name: 'BarChart',
    props: {
        title: String,
        populationData: Object,
        year: Number,
    },
    components: {
        Bar,
    }
}
</script>Header

<style scoped>
    .barChart {
        border: 1px solid steelblue;
        border-radius: 4px;
        text-align: left;
    }
    
    .countries {
        border-top: 1px solid steelblue;
        margin-top: 10px;
        padding-top: 10px;
        margin-bottom: 10px;
        height: 60vh;
        overflow-y: auto;
    }

    .barChart h2 {
        margin: 10px;
    }
</style>