<template>
    <div class="multi-select">
        <SearchBar @click.native="toggleList" />

        <ListDropdown :listAPI="listAPI" :selected="selected" @selectNewOption="updateSelectOption"
            @toggleList="toggleList" v-if="isShow" />

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
