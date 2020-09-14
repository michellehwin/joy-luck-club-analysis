<template>
    <b-container fluid>
        <div class="scrollImage"></div>
        <b-row class="plot-point">
            <b-col col lg="5" id="first-point">
                <h1>Rose's encounter with racism</h1>
                <p>Rose attended an event with Ted, her rich, white boyfriend, and met his parents for the first time. Ted's mother implied that because she was asian, she would bring shame to Ted's family because the people in high society aren't open-minded enough to accept the people of her race. This logically reinforces the idea that the American dream is one slanted towards white culture and gives credibility to the movie because it shows an example of racism that many members of the audience have experienced. It also makes us hope that Rose and Ted will defy the norms and marry for love, not social status.</p>
            </b-col>
        </b-row>
        <b-row align-h="end" class="text-right plot-point">
            <b-col col lg="5" id="second-point">
                <h1>June and her mother make up</h1>
                <p>One night when the Joy Luck Club gathers, Waverly and June get into an argument about June's sub-par work in front of the entire table. June's mother doesn't back her up and implies that Waverly has more style than her. The day after, June tells her mother that she was never enough for her. Suyuan tells her that she's wrong and that she has something that is unique and geniune: kindness. The turning point between June and her mother asserts the mother-daughter relationship that is always there.</p>
            </b-col>
        </b-row>
        <b-row class="plot-point">
            <b-col col lg="5" id="third-point">
                <h1>Waverly "fixes" her mom's hair</h1>
                <p>The day of Waverly's wedding, Waverly meets her mom at an upscale salon for an appointment. Her mom accuses her of being embarrased of her, not even letting her have her Chinese-style perm in front of her white husband's family. Lindo's accusation reveals her insecurity that she is losing her daughter to the American culture, providing credibility to the main theme by portraying an example of an immigrant turning towards American culture.</p>
            </b-col>
        </b-row>
        <b-row align-h="end" class="text-right plot-point">
            <b-col col lg="5" id="fourth-point">
                <h1>Ying-Ying shares her story with Lena</h1>
                <p>Ying-Ying breaks a vase in Lena's bedroom, causing Lena to come to her mom and confront the unhappiness of her marriage. In trying to obtain happiness, Lena forgot who she was. After talking with her mother and learning about her past, Lena knows the first steps in gaining freedom and divorces Harold. After seeing Lena successfully leave a damaging marriage, the audience is enstilled with hope for the daughters. This point in the movie also gives credibility to the mothers and their experiences and proves that the daughters can gain a lot by listening to their mothers. </p>
            </b-col>
        </b-row>
    </b-container>
</template>

<script>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import { MotionPathPlugin } from "gsap/MotionPathPlugin";
gsap.registerPlugin(ScrollTrigger);
gsap.registerPlugin(MotionPathPlugin);

export default {
    methods: {
        getPos: function (el) {
            var div = document.getElementById(el);
            var parent = div.parentElement.parentElement;
            var offsets = div.getBoundingClientRect();
            var x =
                el.includes("second") || el.includes("fourth")
                    ? offsets.left - document.documentElement.clientWidth / 2
                    : offsets.right - document.documentElement.clientWidth / 2;
            var y = offsets.y - parent.getBoundingClientRect().y;
            console.log(`{x: ${x}, y:${y}}`);

            return {
                x: x,
                y: y,
            };
        },
    },
    mounted() {
        // gsap.utils.toArray(".plot-point").forEach((row) => {
        //     ScrollTrigger.create({
        //         trigger: row,
        //         start: "top top",
        //         pin: true,
        //         pinSpacing: false,
        //     });
        // });

        gsap.to(".scrollImage", {
            motionPath: {
                path: [
                    this.getPos("first-point"),
                    this.getPos("second-point"),
                    this.getPos("third-point"),
                    this.getPos("fourth-point"),
                    // { x: 50, y: 50},
                    // { x: 100, y: 100 },
                    // { x: 50, y: 200 },
                    // { x: 100, y: 400 },
                ],
            },
            scrollTrigger: {
                trigger: ".scrollImage",
                start: "center center",
                endTrigger: "#fourth-point",
                end: "center 10%",
                scrub: 1,
                markers: true,
            },
        });
    },
};
</script>

<style scoped>
.scrollImage {
    padding-top: 100px;
    background-image: url("../assets/luck.png");
    width: 100px;
    height: 100px;
    background-size: contain;
    margin-left: auto;
    margin-right: auto;
    /* background-color: blanchedalmond; */
}
.row {
    padding-top: 5rem;
    padding-bottom: 5rem;
    background-color: #fed9b7;
}
p {
    /* font-size: 1.2em; */
}
.row {
    padding: 2%;
}
</style>