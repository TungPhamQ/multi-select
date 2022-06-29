<template>
    <div class="multi-select">
        <SearchBar />
        <ListDropdown :listAPI="listAPI" :selected="selected" @selectNewOption="addNewSelectOption" />
        <SelectResult :selected="selected" @deleteOption="deleteSelectOption" />
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
        addNewSelectOption(e) {
            this.selected = e
        },
        deleteSelectOption(e) {
            this.selected = e;
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
