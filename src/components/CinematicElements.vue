<template>
    <div class="cinematic-elements">
        <h1 class="text-center pt-4">Cinematic Elements</h1>
        <p class="text-center">Hover over text to see more clearly</p>
        <div class="carousel">
            <CarouselElement
                image1="sit-east.png"
                images="1"
                paragraph="June replaces her mother at the mahjong table for the first time since she died at the weekly Joy Luck Club meeting. The sunlight is on her and she sits 'on the East where things begin.' This signifies the new beginnings in store for June. The camera is pointed straight-on June and the aunties sitting in different spots, emphasizing that this movie is about all of their stories and how they each embody something different, but share similarities."
                heading="New Beginnings"
                class="panel"
            />
            <CarouselElement
                image1="eat-old.png"
                image2="eat-young.png"
                images="2"
                paragraph="When Lindo is only four years old, her mother arranges for her to be married to a prince when she turns 15. Until then, her mother trains her to be the most lady-like and proper child as can be. The only scenes where Lindo is seen with her mother are shrounded in darkness, showing the darkness of her mother's moral, knowing that she has to send her daughter away forever. The lighting evokes sorrow and sympathy for Lindo and her mother."
                heading="Sent off for marriage"
                class="panel"
            />
            <CarouselElement
                image1="cin3-1.png"
                image2="cin3-2.png"
                image3="cin3-3.png"
                images="3"
                paragraph="An-Mei's mother was disowned for having affairs with another man shortly after her husband had died. They were reunited when An-Mei's grandmother was dying and An-Mei's mother had come to sacrifice her blood, an old Chinese tradition to save a relative. In these scenes, the camera work was slowed and zoomed into An-Mei, somber music was playing, and shadows were cast on An-Mei's face. These cinematic effects helped impart a feeling of uncertainty of what was to come next and sadness for An-Mei's mother. The scenes following were indeed sad as foreshadowed by the past scenes."
                heading="An-Mei reuinites with her mother"
                class="panel"
            />
            <CarouselElement
                image1="cin4-1.png"
                image2="cin4-2.png"
                image3="cin4-3.png"
                images="3"
                paragraph="During her time married to her husband in China, she was miserable; he would cheat on her almost every night. All of the scenes of her life in China have dim lighting. When she moves to America, she is still sad and recovering from the emotional trauma of her toxic husband and killing her son but there is light shining in through the windows. This indicates that there are better things in store for her future. It also ties into the theme and implies that chasing the American dream is better than living in China."
                heading="Ying-Ying's ascent to freedom"
                class="panel"
            />
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
            xPercent: -100 * (sections.length -1),
            ease: "none",
            scrollTrigger: {
                trigger: ".carousel",
                start: "center 55%",
                pin: true,
                pinSpacing: false,
                scrub: 1,
                markers: true,
                snap: { snapTo: 1 / (sections.length - 1), duration: 0.2 },
                // base vertical scrolling on how wide the container is so it feels more natural.
                end: () =>
                    "+=" + document.querySelector(".cinematic-elements").offsetWidth + 1,
            },
        });
    },
};
</script>

<style scoped>
h1 {
    font-size: 5rem;
    font-weight: 600;
    font-style: italic;
}
.carousel {
    display: flex;
    flex-wrap: nowrap;
    width: 400% !important;
    height: 100vh !important;
}
</style>