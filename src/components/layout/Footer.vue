<template>
        <p class="text text-muted">
            {{footnote}} | {{year}}
        </p>
</template>

<script>
export default {
    name: "Footer",
    props: {
        footnote: String,
        year: String,
    }
}
</script>

<style>
    .text-muted {
        text-align: center;
    }
</style>