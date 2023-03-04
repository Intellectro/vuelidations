<template>
    <div class="container">
        <Header />
        <div class="form-flexbox">
            <Image styled="0.5" :imgpart="source" />
            <Formval size="0.5" />
        </div>
    </div>
</template>

<script>
import Formval from "./components/Form.vue";
import Image from "./components/Image.vue";
import imagepart from "./img/regpic.png";
import Header from "./components/Header.vue";

export default {
    name: "App",
    components: {
        Formval,
        Image,
        Header,
    },
    data() {
        return {
            source: imagepart,
        };
    },
};
</script>

<style scope>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@100;200;300;400;500&family=Poppins:wght@100;200;300;400&display=swap");

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: "Poppins", sans-serif;
}

body {
    overflow-x: hidden;
}

.container {
    width: 100vw;
    min-height: 100vh;
}

.form-flexbox {
    display: flex;
    height: 100%;
}

@media screen and (max-width: 950px) {
    .form-flexbox {
        display: flex;
        flex-direction: column;
    }
}

@media screen and (max-width: 650px) {
    .title {
        font-size: 35px;
        text-align: center;
    }
}

@media screen and (max-width: 350px) {
    .title {
        font-size: 28px;
        text-align: center;
    }
}

@media screen and (max-width: 250px) {
    .title {
        font-size: 19px;
        text-align: center;
    }
}
</style>
