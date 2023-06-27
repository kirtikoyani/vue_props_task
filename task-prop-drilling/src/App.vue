<template>
<div id="app">
    <the-home />
    <pe-home />
    <Homepre />
</div>
</template>

<script>
import TheHome from './components/prop_drilling/TheHome.vue'
import PeHome from './components/provide_inject/PeHome.vue'
import Homepre from './components/provide_inject_methods/HomePeM.vue'

export default {
    name: 'App',
    components: {
        TheHome,
        PeHome,
        Homepre
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
