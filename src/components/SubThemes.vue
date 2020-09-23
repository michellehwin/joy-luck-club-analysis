<template>
    <b-container fluid>
        <b-row>
            <b-col class="d-flex flex-row">
                <div class="main-header flex-shrink">Supporting</div>
                <div class="main-header flex-shrink">Themes</div>
            </b-col>
        </b-row>
        <SubTheme
            themeHeading="Hope drives Life"
            backImageStart="5"
            imageBack="feather.png"
            imageFront="american-dream.jpg"
            frontImageStart="1"
            themeParagraph="At the beginning of the movie, June mentions a swan feather that her mother(Suyuan) left for her. This feather was apart of a swan that Suyuan had bought in China that she had try to bring to America; it represented all of the hope she had for her and her daughter. This hope towards the American dream inadvertantly pushed the American culture onto her daughter, making her turn away from her Chinese roots. June's childhood was riddled with conflicts with her mother because she couldn't understand her mother's intentions and Chinese ways. Hope for a better life is what also drove the mothers to survive all of their hardships in China. The constant role that hope plays in moving the character's lives forward demonstrates that hope if the driving force of life." 
            imagePaddingTop="20"
        />
        <SubTheme
            backImageStart="1"
            imageBack="sacrifice-1.png"
            imageFront="sacrifice-2.png"
            backImageSpan=8
            :textLeft="false"
            frontImageStart="7"
            descriptionStart="9"
            descriptionPaddingLeft="15"
            imagePaddingTop="20"
            descriptionPaddingRight="0"
            themeHeading="Sacrifice "
            themeParagraph="To come to America and guarantee a good future for their daughters, the mothers had to abandon their home country, something that takes great courage. Both the mothers and daughters also have to sacrifice part of their culture, having to choose between embodying the Chinese or American way in large and small ways, losing something no matter what they pick. The daughters mostly stick to American customs and lose the connection they have to their homeland and their mothers but gain prestiege in the American society. The mothers mainly stick to Chinese traditions, causing their daughters to be embarassed of them at times, but have a better sense of identity. The numerous sacrifices made by the characters both in their daily lives and in monumental moments show that sacrifice is an ultimate gesture of love."
        />
        <SubTheme
            themeHeading="Storytelling "
            backImageStart="5"
            imageBack="story-1.png"
            imageFront="story-2.png"
            themeParagraph="Storytelling is a powerful tool that can help bridge cultural and language barries. Because the daughters grow up learning English and the mothers mainly speak Chinese, it's difficult for them to communicate with each other. To overcome this barrier, the mothers tell stories of their past lives in hopes that their daughters learn the lessons they had to learn the hard way. The daughters struggle with their cultural identity and consequently their self-identity because of the pressures the American dream and their mothers put onto them. Through their mother's stories, they learn to bridge the gap and find themselves along the way."
        />
        <SubTheme
            backImageStart="1"
            backImageSpan=8
            frontImageStart="5"
            imageBack="mask-2.png"
            imageFront="mask-1.png"
            :textLeft="false"
            descriptionStart="9"
            descriptionPaddingLeft="15"
            descriptionPaddingRight="0"
            themeHeading="Hiding Behind a Mask"
            themeParagraph="Trying to pursure the American dream whilst pleasing their mothers, the daughters put on a happy face, but underneath the mask, they are lost in life. Lena appears happy with Harold, but in reality, she conforms to his liking, doesn't speak up, and doesn't know what she wants in life. Rose is also stuck in a loop of conformity, losing herself to her husband's wishes. The daughters are so caught up with appearing happy and seeming successful that they forget where they came from and their source of happiness in life. The face they put on when in public and with their families differs greatly from the reality of their situation, showing that people are not always what they seem."
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