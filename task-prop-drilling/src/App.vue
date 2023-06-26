<template>
<div id="app">
    <the-home />
    <pe-home/>
</div>
</template>

<script>
import TheHome from './components/prop_drilling/TheHome.vue'
import PeHome from './components/provide_inject/PeHome.vue'

export default {
    name: 'App',
    components: {
        TheHome,
        PeHome
    }
}
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
}
</style>
