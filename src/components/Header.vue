<template>
    <header>
        <h1>{{ title }}</h1>
        <h1 id="globe">&#127760;</h1>
    </header>
</template>

<script>

export default {
    name: 'Header',
    props: {
        title: String,
    },
    components: {
    }
}
</script>

<style scoped>
    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        height: 40px;
    }

    #globe {
        color: steelblue;
    }
</style>