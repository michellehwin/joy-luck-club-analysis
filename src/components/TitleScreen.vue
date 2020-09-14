<template>
    <b-container fluid class="text-center">
        <!-- <b-button @click="show = !show">Toggle render</b-button> -->
        <transition name="fade" enter-active-class="animate__animated animate__fadeIn">
            <div v-if="show">
                <h1>The Joy Luck Club</h1>
                <h2>A Dynamic Movie Analysis</h2>
                <p>Best if viewed on a laptop/computer</p>
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
    font-size: 4rem;
    font-weight: bold;
}
@media (min-width: 992px) {
    h1 {
        font-size: 10rem;
    }
}
.container-fluid {
    padding-top: 20%;
    padding-bottom: 25%;
}
.animate__animated.animate__fadeIn {
    --animate-duration: 0.4s;
}
</style>