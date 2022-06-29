<template>
    <div id="app">
        <MultiSelection :listAPI="listAPI" />
    </div>
</template>

<script>
import MultiSelection from "./components/MultiSelection.vue";
import axios from "axios";

export default {
    name: "App",
    data() {
        return {
            listAPI: Array,
        };
    },
    components: {
        MultiSelection,
    },
    created() {
        axios
            .get("https://provinces.open-api.vn/api/")
            .then((response) => (this.listAPI = response.data));
    },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Noto+Sans:wght@100;200;300;400;500;600;700;800&display=swap");

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: "Noto Sans", sans-serif;
}
</style>
