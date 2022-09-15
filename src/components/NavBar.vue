<template>
    <div class="navbar" :class="open ? 'opened' : 'closed'" @click="toggleStatus()">
        <div v-if="open">
            <p>Productos</p>
            <p>Bar</p>
            <p>Nosotros</p>
            <p>Contacto</p>
            <p>Mi cuenta</p>
        </div>
    </div>
</template>

<script>
export default {
    name:'NavBar',
    data(){return{
        open:false,
    }},
    methods:{
        toggleStatus(){
            this.open = !this.open
        }
    },
}
</script>

<style scoped>
.navbar{
    background: green;
}
.opened{
    width: 500px;
}
.closed{
    width: 100px;
}

</style>