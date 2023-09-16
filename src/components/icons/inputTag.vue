<script>
export default{
    props:["onTagsChangue"],
    data(){
        return{
            currentValue:'',
            tags:[],

        }
    },
    methods:{
        handleKeyDown(e){
            if(e.key==='Enter'){
                let Exist = this.tags.some(item => item==this.currentValue) 
                Exist ? console.log('este item ya existe!') : this.tags.push(this.currentValue)
                this.onTagsChangue(this.tags)
                this.currentValue=''
            }else if(e.key=='Backspace' && this.currentValue== ''){
                this.tags.pop()
                this.onTagsChangue(this.tags)
            }
        },
        deleted(tag){
            this.tags=this.tags.filter(index =>{
                return tag!=index
                
            })
            this.onTagsChangue(this.tags)
        }   
    }
}

</script>


<template>
    <div class="inputTab">
        <div class="tab">
            <input v-model="currentValue" type="text" @keydown="handleKeyDown">
        </div>

        <div class="tags" v-for="(tag, index) in tags" :key="index">
            {{ tag }}
            <button @click="deleted(tag)">x</button>
        </div>
    </div>
</template>

<style>
.inputTab{
    display: flex;   
    padding: 3px;
    
}
.inputTab input{
    border: 1px solid black;
    border-radius: 5px;
}
.tags{
   margin-left: 5px ;
   padding: 2px 5px;
   border: 1px solid black;
   border-radius: 5px;
}
.tags button{
    background: red;
    border-radius: 5px;
    font-weight: bold;
    cursor: pointer;
}
.tags :hover{
    background-color: #ccc;
}
</style>