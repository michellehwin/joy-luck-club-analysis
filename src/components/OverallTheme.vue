<template>
    <b-container fluid class="text-center" id="overallTheme">
        <b-row align-h="center">
            <b-col cols="9">
                <h1>Theme</h1>
                <p>The American dream implies that in order to be succesful, you most conform towards the culture of white people.</p>
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
            duration: .5,
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
    font-size: 4em;
}
p {
    font-size: 2rem;
}
</style>