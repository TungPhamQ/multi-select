<template>
    <div class="select-result">
        <div v-for="item in selectedOptions" :key="item">
            {{ item }}
            <img src="../assets/close.png" @click="deleteOption(item)">
        </div>
    </div>
</template>

<script>
export default {
    name: 'SelectResult',
    data() {
        return {
            selectedOptions: [],
        }
    },
    props: {
        selected: Array,
    },
    methods: {
        deleteOption(item) {
            console.log(item);
            this.selectedOptions = this.selectedOptions.filter(data => data !== item);
        }
    },
    watch: {
        selected: {
            immediate: true,
            handler() {
                this.selectedOptions = this.selected
            }
        },
        selectedOptions() {
            this.$emit('deleteOption', this.selectedOptions)
        }

    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.select-result {
    width: 100%;
    border: 1px solid #ccc;
    min-height: 48px;
}

.select-result img {
    width: 11px;
    height: 11px;
    margin: 0px 11px 0px 11px;
}
</style>
