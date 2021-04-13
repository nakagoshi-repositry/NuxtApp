<template>
<v-container>
    <div id="app">
    <v-form id ="memoList" v-on:submit.prevent >
        <v-list v-for="item in todos"
                v-bind:todo="item"
                v-bind:key="item.id">

            <v-card-text v-model="newItem" 
                    aria-placeholder="ここに入力"></v-card-text>
            <v-btn v-on:click="addItem" float:right 
                max-height: 5px
                max-width: 5px;>+</v-btn>
        </v-list>
    </v-form>
    </div>
</v-container>
</template>
<script>
import vue from 'vue'
 export default vue.extend({
    
    props:{
        id:Number,
        memo:String,
        item:String    
    },

    data ()  {  
        return{
            newItem:'',
            todos:[]
        }
       
    },
    
    methods:{
        addItem: function(event){
           if(this.newItem == '')return;
        
            let memo = {
                item: this.newItem,
                isdone:false
            };
           this.todos.push(memo);
           this.newItem = ' ' ;
        }
    }
})
</script>
<style>

</style>