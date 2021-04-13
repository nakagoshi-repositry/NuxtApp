<template>

    <v-card  id = "memoCard" >
        <TodoList />
    </v-card>
</template>

<script>
import TodoList from   '~/components/TodoList.vue'
export default {
    components:{
        TodoList
    }
}
</script>
<style>
#memoCard{
    border: 1px solid darkblue;
    height: 300px;
    width: 300px;
}


</style>