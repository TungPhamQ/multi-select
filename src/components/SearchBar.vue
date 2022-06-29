<template>
    <div class="search-bar">
        <input type="text" placeholder="Chọn tỉnh thành: " class="search-input">
    </div>
</template>

<script>
export default {
    name: 'SearchBar',

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.search-input {
    width: 470px;
    height: 48px;
    border: 1px solid #999;
    border-radius: 4px;

    font-weight: 400;
    font-size: 16px;
    line-height: 24px;
    padding-left: 10px;
}
</style>
