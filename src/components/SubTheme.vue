<template>
    <b-row class="subtheme" :id="id">
        <div class="subtheme-description" :style="descriptionStyle">
            <h1>{{themeHeading}}</h1>
            <p>{{themeParagraph}}</p>
        </div>
        <div class="image-front" :style="frontImageStyle">
            <!-- <img src="https://picsum.photos/id/1003/700/400"/> -->
            <img
                :src="require('@/assets/' + imageFront + '')"
                :style="{paddingTop: imagePaddingTop+ 'px'}"
            />
        </div>
        <div class="image-bottom" :style="backImageStyle">
            <!-- <img src="https://picsum.photos/id/10/700/400" alt /> -->
            <img :src="require('@/assets/' + imageBack + '')" />
        </div>
    </b-row>
</template>

<script>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

export default {
    props: {
        imageBack: { default: "filler.jpg" },
        imageFront: { default: "filler.jpg" },
        themeHeading: { default: "Lorem Ipsum" },
        themeParagraph: {
            default:
                "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Itaque nisi eligendi voluptates corrupti architecto libero aut inventore sunt rem ab laudantium, velit omnis explicabo natus excepturi a perferendis corporis praesentium.",
        },
        backImageStart: { default: 4 },
        backImageSpan: { default: 9 },
        frontImageStart: { default: 2 },
        frontImageSpan: { default: 6 },
        descriptionStart: { default: 1 },
        descriptionPaddingRight: { default: 15 },
        descriptionPaddingLeft: { default: 0 },
        imagePaddingTop: { default: 0 },
        textLeft: { default: true}
    },
    computed: {
        id: function () {
            return this.themeHeading.substr(0, this.themeHeading.indexOf(" "));
        },
        backImageStyle: function () {
            return {
                gridRow: 1,
                gridColumn:
                    this.backImageStart + "/ span " + this.backImageSpan,
            };
        },
        frontImageStyle: function () {
            return {
                gridRow: 1,
                gridColumn:
                    this.frontImageStart + "/ span " + this.frontImageSpan,
                paddingTop: "60%",
                paddingBottom: "10%",
                zIndex: 1,
            };
        },
        descriptionStyle: function () {
            console.log(this.textLeft);
            let left; this.textLeft ? left = "left" : left = "right";
            console.log({left});
            return {
                textAlign: left,
                zIndex: 2,
                gridColumn: this.descriptionStart + "/ span 4",
                gridRow: 1,
                paddingRight: this.descriptionPaddingRight + "px",
                paddingLeft: this.descriptionPaddingLeft + "px",
            };
        },
    },
    mounted() {
        console.log(this.textLeft);
        gsap.fromTo(
            "#" + this.id + " .image-bottom",
            {
                opacity: 0,
                duration: 0,
            },
            {
                scrollTrigger: {
                    trigger: "#" + this.id + " .image-bottom",
                    start: "top 80%",
                    // markers: true,
                    toggleActions: "restart none none reverse",
                },
                opacity: 1,
                duration: 0.3,
                clipPath: "polygon(0 0, 100% 0, 100% 100%, 0% 100%)",
            }
        );
        gsap.fromTo(
            "#" + this.id + " .image-front",
            {
                opacity: 0,
                duration: 0,
            },
            {
                scrollTrigger: {
                    trigger: "#" + this.id + " .image-front",
                    start: "top 80%",
                    // markers: true,
                    toggleActions: "restart none none reverse",
                },
                opacity: 1,
                duration: 0.3,
                clipPath: "polygon(0 0, 100% 0, 100% 100%, 0% 100%)",
            }
        );
        gsap.from("#" + this.id + " h1", {
            scrollTrigger: {
                trigger: "#" + this.id + " h1",
                start: "bottom 95%",
                // markers: true,
                toggleActions: "restart pause resume reverse",
            },
            opacity: 0,
            ease: "power4.out",
            duration: 0.3,
            y: 30,
        });
        gsap.from("#" + this.id + " p", {
            scrollTrigger: {
                trigger: "#" + this.id + " p",
                start: "top 80%",
                // markers: true,
                toggleActions: "restart pause resume reverse",
            },
            opacity: 0,
            ease: "power4.out",
            duration: 0.3,
            y: 30,
        });
    },
};
</script>

<style scoped>
.subtheme {
    display: grid;
    position: relative;
    grid-template-columns: repeat(12, 1fr);
    padding-bottom: 5%;
}

/* p {
    font-size: 1.2em !important;
} */
img {
    width: 100%;
    display: block;
}
</style>