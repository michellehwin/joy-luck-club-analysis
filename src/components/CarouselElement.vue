<template>
    <section class="parent">
        <div class="explanation">
            <h1 class="text-center">{{heading}}</h1>
            <p>{{paragraph}}</p>
        </div>
        <div class="image image-1" :style="image1Style">
            <img :src="require('@/assets/' + image1 + '')" alt />
        </div>
        <div v-if="images >1" class="image image-2" :style="image2Style">
            <img :src="require('@/assets/' + image2 + '')" alt />
        </div>
        <div v-if="images >2" class="image image-3">
            <img :src="require('@/assets/' + image3 + '')" alt />
        </div>
    </section>
</template>

<script>
export default {
    props: ["image1", "image2", "image3", "heading", "paragraph", "images"],
    computed: {
        image1Style: function () {
            let style;
            this.images == 1
                ? (style = {
                      gridArea: "1 / 1 / 4 / 13",
                  })
                : (this.images == 2
                      ? (style = {
                            gridArea: "1 / 1 / 4 / 7",
                        })
                      : (style = {
                            gridArea: "1 / 1 / 4 / 5",
                        }));
            console.log(style);
            return style;
        },
        image2Style: function () {
            let style;
            this.images == 2
                ? (style = {
                      gridArea: "1 / 7 / 4 / 13",
                  })
                : (style = {
                      gridArea: "1 / 5 / 4 / 9",
                  });
            console.log(style);
            return style;
        },
    },
};
</script>

<style scoped>
p{
    font-size: 1.2em;
}
.parent {
    /* background-color: pink; */
    display: grid;
    flex: 1;
    position: relative;
    grid-template-columns: repeat(12, 1fr);
    grid-template-rows: repeat(3, 1fr);
    /* grid-column-gap: 2%; */
    /* margin-top: 100px; */
    margin-bottom: 100px;
}
.explanation {
    padding: 20px;
    background-color: rgba(255, 255, 255, 0.2);
    grid-area: 2 / 3 / 3 / 11;
    z-index: 1;
}
.explanation:hover {
        background-color: rgba(255, 255, 255, 1);

}
img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}
.image {
    /* max-width: 100%; */
    height: 100%;
    overflow: hidden;
    min-width: 0;
    grid-row: 1/3;
    padding-left: 5%;
    padding-right: 5%;
}
.image-2 {
    grid-area: 1 / 5 / 4 / 9;
}
.image-3 {
    grid-area: 1 / 9 / 4 / 13;
}
</style>