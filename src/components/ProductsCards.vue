<template>
    <div align="center">
        <h3>{{product.name}}</h3>
        <p>{{product.cantidad}}</p>
        <p>{{product.price}}</p>
    </div>
</template>

<script>
export default {
    props:{
        product: Object
    }
}
</script>

<style>

</style>
