<template>
    <div class="cinematic-elements">
        <div class="carousel">
            <CarouselElement image="../../public/filler.jpg" paragaph="lorem" heading="lorem" class="panel" />
            <CarouselElement image="../../public/filler.jpg" paragaph="lorem" heading="lorem" class="panel" />
            <CarouselElement image="../../public/filler.jpg" paragaph="lorem" heading="lorem" class="panel" />
            <CarouselElement image="../../public/filler.jpg" paragaph="lorem" heading="lorem" class="panel" />

        </div>
    </div>
</template>

<script>
import CarouselElement from "./CarouselElement";
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

export default {
    components: { CarouselElement },
    mounted() {
        console.log(document.querySelector(".carousel").offsetWidth);
        let sections = gsap.utils.toArray(".panel");
        gsap.to(sections, {
            xPercent: -100 * (sections.length - 1),
            ease: "none",
            scrollTrigger: {
                trigger: ".carousel",
                pin: true,
                pinSpacing: false,
                scrub: 1,
                markers: true,
                snap: 1 / (sections.length - 1),
                // base vertical scrolling on how wide the container is so it feels more natural.
                end: () =>
                    "+=" + document.querySelector(".carousel").offsetWidth,
            },
        });
    },
};
</script>

<style scoped>
.carousel{
    display:flex;
    flex-wrap: nowrap;
    width:400% !important;
    height:100vh !important;
}
</style>