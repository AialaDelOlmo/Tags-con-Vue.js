<script>
    export default{
        data() {
            return{
                currentValue: "",
                tags: ['un', 'dos', 'tres'],
            }
        }
    }
</script>

<template>
    <div class="inputTag">
        <div class="tags">
            <div class="tag" v-for="(tag, index) in tags" :key="index">
                {{ tag }}
            </div>
        </div>
    <input type="text" v-model="currentValue">
    </div>
</template>

<style scoped>

</style>