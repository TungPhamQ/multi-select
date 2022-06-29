<template>
    <div class="multi-select">
        <SearchBar @click.native="toggleList" @search="getSearch" />

        <ListDropdown :listAPI="listAPI" :selected="selected" @selectNewOption="updateSelectOption"
            @toggleList="toggleList" v-if="isShow" :search="search" />

        <SelectResult :selected="selected" @deleteOption="updateSelectOption" v-if="!isShow && selected.length > 0" />
    </div>
</template>

<script>
import SearchBar from "./SearchBar.vue";
import ListDropdown from "./ListDropdown.vue";
import SelectResult from "./SelectResult.vue";
export default {
    name: 'MultiSelection',
    data() {
        return {
            selected: [],
            isShow: false,
            search: '',
        }
    },
    components: {
        SearchBar,
        ListDropdown,
        SelectResult
    },
    props: {
        listAPI: null,
    },
    methods: {
        updateSelectOption(e) {
            this.selected = e
        },

        toggleList() {
            this.isShow = !this.isShow;
        },

        getSearch(e) {
            this.search = e;
        }

    }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.multi-select {
    margin: auto;
    width: 480px;
    box-sizing: border-box;
    margin-top: 100px;
}
</style>
