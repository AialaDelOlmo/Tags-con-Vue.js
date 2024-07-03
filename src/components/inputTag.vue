<script>
    export default{
        emits: ["onTagsChange"],
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
                //this.onTagsChange(this.tags);
                this.$emit('onTagsChange', this.tags);
            }
        },
        handleSubmit(){
            if(this.currentValue != ""){
                const exits = this.tags.some(item => item === this.currentValue)
                if(!exits){
                    this.tags.push(this.currentValue);
                    this.currentValue="";
                    //this.onTagsChange(this.tags);
                    this.$emit('onTagsChange', this.tags);
                }
            }
        },
        deleteTag(tag){
            this.tags = this.tags.filter(item => item != tag);
            //this.onTagsChange(this.tags);
            this.$emit('onTagsChange', this.tags);
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
    .inputTag{
        display: inline-flex;
        border: solid 1px #000000;
        border-radius: 3px;
        height: 43px;
    }
    .tags{
        display: flex;
        gap: 3px;
        padding: 5px;
    }
    .tags .tag {
        display: flex;
        padding: 5px;
        border: solid 1px #cccc;
        gap: 5px;
        align-content: center;
        border-radius: 3px;
    }
    .inputTag form {
        display: inline-flex;
    }
    .inputTag .input {
        border: none;
        outline: none;
        padding: 0px 5px;
    }
    .inputTag button {
        background-color: transparent;
        border: none;
        border-radius: 3px;
        cursor: pointer;
    }
    .tag button:hover {
        background-color: #eeee;
    }
</style>