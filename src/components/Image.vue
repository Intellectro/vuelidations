<template>
    <div :style="{ flex: styled }" class="image-con">
        <img :src="imgpart" :alt="imagepart" />
    </div>
</template>

<script>
export default {
    name: "Image",
    props: ["imgpart", "styled"],
};
</script>

<style scope>
img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center;
    image-rendering: pixelated;
}
</style>
