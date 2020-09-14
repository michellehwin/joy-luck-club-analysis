<template>
    <b-container fluid class="text-center" id="overallTheme">
        <b-row align-h="center">
            <b-col cols="9">
                <h1>Theme</h1>
                <p>The American dream implies that in order to be succesful, immigrants must erase their natal traditions and conform to "white" culture.</p>
            </b-col>
        </b-row>
    </b-container>
</template>

<script>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

export default {
    mounted() {
        gsap.from("#overallTheme", {
            scrollTrigger: {
                trigger: "#overallTheme p",
                start: "top 70%",
                // markers: true,
                toggleActions: "restart pause resume reverse",
            },
            opacity: 0,
            duration: 0.5,
            xPercent: -50,
        });
    },
};
</script>

<style scoped>
.container-fluid {
    padding-bottom: 25%;
}
h1 {
    font-weight: 600;
    font-style: italic;
    font-size: 3em;
}
p {
    font-size: 1.2rem;
}
@media (min-width: 992px) {
    h1 {
        font-size: 4rem;
    }
    p {
        font-size: 2rem;
    }
}
</style>