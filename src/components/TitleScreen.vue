<template>
    <b-container fluid class="text-center">
        <!-- <b-button @click="show = !show">Toggle render</b-button> -->
        <transition name="fade" enter-active-class="animate__animated animate__fadeIn">
            <div v-if="show">
                <h1>The Joy Luck Club</h1>
                <h2>A Dynamic Movie Analysis</h2>
            </div>
        </transition>
    </b-container>
</template>

<script>
export default {
    data: function () {
        return { show: false };
    },
    mounted() {
        this.show = true;
    },
};
</script>

<style scoped>
h1 {
    padding-bottom: 30px;
    font-size: 10em;
    font-weight: bold;
}
.container-fluid {
    padding-top: 20%;
    padding-bottom: 25%;
}
.animate__animated.animate__fadeIn {
    --animate-duration: 0.4s;
}
</style>