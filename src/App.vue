<template>
    <div id="app">
        <MultiSelection :listAPI="listAPI" />
    </div>
</template>

<script>
import MultiSelection from './components/MultiSelection.vue'
import axios from 'axios'

export default {
    name: 'App',
    data() {
        return {
            listAPI: Array
        }
    },
    components: {
        MultiSelection
    },
    mounted() {
        axios
            .get('https://provinces.open-api.vn/api/')
            .then(response => (this.listAPI = response.data))
    },

}
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
</style>
