<template>
    <b-container fluid>
        <b-row>
            <b-col class="d-flex flex-row">
                <div class="main-header flex-shrink">Supporting</div>
                <div class="main-header flex-shrink">Themes</div>
            </b-col>
        </b-row>
        <SubTheme
            themeHeading="Hope drives life"
            themeParagraph="At the beginning of the movie, June mentions a swan feather that her mother(Suyuan) left for her. This feather was apart of a swan that Suyuan had bought in China that she had try to bring to America; it represented all of the hope she had for her and her daughter. This hope towards the American dream inadvertantly pushed the American culture onto her daughter, making her turn away from her Chinese roots. The American Dream implies that to be successful, you have to behave like white people do."
            imagePaddingTop=150
        />
        <SubTheme
            backImageStart="1"
            frontImageStart="7"
            descriptionStart="10"
            descriptionPaddingLeft="15"
            imagePaddingTop=50
            descriptionPaddingRight="0"
            themeHeading="Sacrifice "
            themeParagraph="Sacrifice is the ultimate demonstration of love. To come to America and guarantee a good future for their daughters, the mothers had to abandon their home country, a great sacrifice. \n Both the mothers and daughters also have to sacrifice part of their culture. They have to choose between embodying the Chinese or American culture, losing something no matter what they pick."
        />
        <SubTheme
            themeHeading="Storytelling "
            themeParagraph="Because the daughters grow up learning English and the mothers mainly speak Chinese, it's difficult for them to communicate with each other. To overcome this barrier, the mothers tell stories of their past lives in hopes that their daughters will see how they fought past their hardships and learn the lessons they had to learn the hard way. "
        />
        <SubTheme
            backImageStart="1"
            frontImageStart="3"
            descriptionStart="10"
            descriptionPaddingLeft="15"
            descriptionPaddingRight="0"
            themeHeading="Hiding Behind a Mask"
            themeParagraph="Trying to pursure the American dream and pleasing their mothers, the daughters appear to be happy. Underneath the mask, they are lost in life. "
        />
    </b-container>
</template>

<script>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);
import SubTheme from "./SubTheme";

export default {
    components: { SubTheme },
    mounted() {
        gsap.from(".main-header", {
            scrollTrigger: {
                trigger: ".main-header",
                start: "center 85%",
                toggleActions: "restart pause resume reverse",
            },
            opacity: 0,
            ease: "power4.out",
            duration: 0.3,
            y: 30,
            stagger: 0.1,
        });
    },
};
</script>

<style scoped>
.main-header {
    font-size: 5rem;
    font-weight: 600;
    font-style: italic;
    padding-bottom: 40px;
    padding-right: 20px;
}
.container-fluid {
    padding-right: 3%;
    padding-left: 3%;
}
</style>