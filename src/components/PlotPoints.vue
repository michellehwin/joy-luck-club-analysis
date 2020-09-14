<template>
    <b-container fluid>
        <div class="scrollImage"></div>
        <b-row>
            <b-col col lg="5" id="first-point">
                <h1>Rose's encounter with racism</h1>
                <p>Rose attended an event with Ted, her rich, white boyfriend, and met his parents for the first time. Ted's mother implied that because she was asian, she would bring shame to Ted's family because the people in high society aren't open-minded enough to accept the people of her race. This logically reinforces the idea that the American dream is one slanted towards white culture and gives credibility to the movie because it shows an example of racism that many members of the audience have experienced. It also makes us hope that Rose and Ted will defy the norms and marry for love, not social status.</p>
            </b-col>
        </b-row>
        <b-row align-h="end">
            <b-col col lg="5" id="second-point">
                <h1>June and her mother make up</h1>
                <p>One night when the Joy Luck Club gathers, Waverly and June get into an argument about June's sub-par work in front of the entire table. June's mother doesn't back her up and implies that Waverly has more style than her. </p>
            </b-col>
        </b-row>
        <b-row>
            <b-col col lg="5" id="third-point">
                <h1>Waverly taking her mom to get her hair "fixed"</h1>
                <p>The day of Waverly's wedding, </p>
            </b-col>
        </b-row>
        <b-row align-h="end">
            <b-col col lg="5" id="fourth-point">
                <h1>Plot Point</h1>
                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Id, hic veritatis. Praesentium autem ex nemo assumenda recusandae architecto molestiae atque soluta laborum! Iure delectus nisi soluta deserunt nam, sequi ad.</p>
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
    background-image: url("../../public/redCircle.png");
    width: 100px;
    height: 100px;
    background-size: contain;
    margin-left: auto;
    margin-right: auto;
}
.row {
    padding-top: 5rem;
    padding-bottom: 5rem;
    background-color: blanchedalmond;
}
p {
    font-size: 1.2em;
}
.row {
    padding: 2%;
}
</style>