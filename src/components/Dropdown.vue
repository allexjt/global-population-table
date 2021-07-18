<template>
    <div class="dropdownContainer">
        <label for ="years">For the year</label>
        <select name="years" id="years">
            <option :key="year" v-for="year in years">{{ year }}</option>
        </select>
    </div> 
</template>

<script>
export default {
    name: 'Dropdown',
    props: {
        years: Array,
    }
}
</script>

<style scoped>
    .dropdownContainer {
        text-align: left;
        margin-bottom: 10px;
        font-size: 20px;
    }

    label {
        margin-right: 5px;
    }

    select {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        font-size: 18px;
        color: steelblue;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        display: inline;  
        border: 0;
        width: fit-content;
        outline: none;
        -webkit-appearance: none;
        -moz-appearance: none;
        border-bottom: 2px solid steelblue;
        transition: all .4s ease-in-out;
    }
    
    select:hover {
        cursor: pointer;   
        color: rgba(70, 130, 180, 0.7); 
    }
    
    option {
        border: 0;
        border-bottom: 1px solid black;
        -webkit-appearance: none;
        -moz-appearance: none;
    }
</style>