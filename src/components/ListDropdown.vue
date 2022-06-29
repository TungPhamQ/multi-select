<template>
    <div class="list-dropdown">
        <div class="list-scroll">
            <div v-for="item in listAPI" :key="item.code">
                <label>
                    <input type="checkbox" :value="item.name" @input="selectNewOption" v-model="selectedOptions">
                    {{ item.name }}
                </label>
            </div>
        </div>

        <div class="button">
            <button>Đồng ý</button>
            <button>Hủy</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ListDropdown',
    data() {
        return {
            selectedOptions: [],
        }
    },
    props: {
        listAPI: null,
        selected: Array,
    },
    methods: {
        selectNewOption: function ($event) {
            const index = this.selectedOptions.indexOf($event.target.value);
            if (index == -1) {
                this.selectedOptions.push($event.target.value);
            }
            else {
                this.selectedOptions.splice(index, 1);
            }
        },
    },
    watch: {
        selected: {
            immediate: true,
            handler() {
                this.selectedOptions = this.selected
            }
        },
        selectedOptions: {
            immediate: true,
            handler() {
                this.$emit('selectNewOption', this.selectedOptions)
            }
        },
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.list-dropdown {
    position: relative;
    margin: auto;
    width: 100%;
    height: 304px;
    align-items: center;
    background: #FFFFFF;
    box-shadow: 0px 1px 8px rgba(102, 102, 102, 0.2);
}

.list-scroll {
    overflow-y: scroll;
    height: 304px;
}

.button {
    position: absolute;
    bottom: 0px;
    background-color: #fff;
    display: block;
    width: 100%;
    padding: 8px 0px 16px 16px;
}
</style>
