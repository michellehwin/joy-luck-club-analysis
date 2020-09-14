<template>
    <div id="app">
        <TitleScreen />
        <OverallTheme />
        <SubThemes />
        <PlotPoints />
        <CinematicElements />
    </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import TitleScreen from "./components/TitleScreen.vue";
import OverallTheme from "./components/OverallTheme.vue";
import SubThemes from "./components/SubThemes.vue";
import CinematicElements from "./components/CinematicElements.vue";
import PlotPoints from "./components/PlotPoints.vue";
export default {
    name: "App",
    components: {
        CinematicElements,
        PlotPoints,
        OverallTheme,
        TitleScreen,
        SubThemes,
    },
};
</script>

<style>
body {
    background-color: #cd5c5c !important;
    font-family: 'Poppins', sans-serif !important;
}
</style>
