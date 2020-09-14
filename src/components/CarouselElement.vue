<template>
    <section class="parent">
        <div class="explanation">
            <h1>{{heading}}</h1>
            <p>{{paragraph}}</p>
        </div>
        <div class="image image-1">
            <img :src="image" alt />
        </div>
        <div class="image image-2">
            <img :src="image" alt />
        </div>
        <div class="image image-3">
            <img :src="image" alt />
        </div>
    </section>
</template>

<script>
export default {
    props: [
        'image','heading', 'paragraph'
    ]
};
</script>

<style scoped>
.explanation {
    background-color: white;
    z-index: 1;
}
.parent {
    background-color: pink;
    display: grid;
    flex:1;
    position: relative;
    grid-template-columns: repeat(12, 1fr);
    grid-template-rows: repeat(3, 1fr);
    /* grid-column-gap: 2%; */
    margin-top: 100px;
    margin-bottom: 100px;
}
.explanation {
    padding: 20px;
    grid-area: 2 / 3 / 3 / 11;
    z-index: 1;
}
.image {
    max-width: 100%;
    height: auto;
    object-fit: contain;
    overflow: hidden;
    min-width: 0;
    grid-row: 1/3;
    padding-left: 10%;
    padding-right: 10%;
}
.image-1 {
    grid-area: 1 / 1 / 4 / 5;
}
.image-2 {
    grid-area: 1 / 5 / 4 / 9;
}
.image-3 {
    grid-area: 1 / 9 / 4 / 13;
}
</style>