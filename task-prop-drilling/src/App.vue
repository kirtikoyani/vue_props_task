<template>
<div id="app">
    <the-home />
    <pe-home />
    <Homepre />
    <home-event-bus/>
    <event-bus-home/>
    <!-- <parent-comp/> -->
</div>
</template>

<script>
// import ParentComp from './components/Event-Bus/parentComp.vue'
import TheHome from './components/prop_drilling/TheHome.vue'
import PeHome from './components/provide_inject/PeHome.vue'
import Homepre from './components/provide_inject_methods/HomePeM.vue'
import HomeEventBus from './components/Event-Bus/HomeEventBus.vue'
import EventBusHome from './components/Event-Bus-Method2/EventBusHome.vue'


export default {
    name: 'App',
    components: {
        TheHome,
        PeHome,
        Homepre,
        // ParentComp,
        HomeEventBus,
        EventBusHome
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
