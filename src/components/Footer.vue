<template>
    <p class="footer" :class="size" >{{ text }}</p>
</template>

<script>
export default {
    name: "Footer",
    props: {
        text: String,
        size: String,
    }
}
</script>

<style scoped>
    .footer {
        text-align: left;
        margin-top: 10px;
        margin-bottom: 0;
    }
    .small {
        font-size: 12px;
        font-style: italic;
        margin-top: 2px;
        color: gray;
    }
</style>