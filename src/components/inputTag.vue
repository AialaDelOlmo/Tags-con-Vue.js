<script>
    export default{
        data() {
            return{
                currentValue: "",
                tags: [],
            
        };
    },
    methods: {
        handlekeyDown(e){
            if(e.key ==='Backspace' && this.currentValue == ""){
               // this.tags.push(this.currentValue);
                //this.currentValue="";
                this.tags.pop();
            }
        },
        handleSubmit(){
            if(this.currentValue != ""){
                const exits = this.tags.some(item => item === this.currentValue)
                if(!exits){
                    this.tags.push(this.currentValue);
                    this.currentValue="";
                }
            }
        },
        deleteTag(tag){
            this.tags = this.tags.filter(item => item != tag);
        }
    }
}
</script>

<template>
    <div class="inputTag">
        <div class="tags">
            <div class="tag" v-for="(tag, index) in tags" :key="index">
                {{ tag }}
                <button @click="deleteTag(tag)">X</button>
            </div>
        </div>
        <form @submit.prevent="handleSubmit">
            <input type="text" v-model="currentValue" @keydown="handlekeyDown">
        </form>
    </div>
</template>

<style scoped>

</style>