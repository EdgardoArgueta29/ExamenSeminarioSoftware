<template>
  <div>
    <h4>{{intercambio}}</h4>
    <h6 class="text-muted">{{moneda}}</h6>
  </div>
</template>

<script>
    export default {
        name: "Par",
        props: {
            moneda: {
                type: String,
                required: true
            },
            intercambio: {
                type: Number,
                required: true
            }
        }
    }
</script>

<style scoped>

</style>
