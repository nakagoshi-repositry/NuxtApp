<template>
    <v-app class="MemoList" color = "primary">
     
        <MemoCard />
        <v-btn id ="addCard">addCard</v-btn>
    </v-app>
</template>
<script>
import MemoCard from '~/components/MemoCard.vue'
import vue from 'vue/dist/vue.esm'

export default {
    compornents:{
        'countmemo':MemoCard
    }


}
</script>

<style>
    #addCard{
        width: 5px;
        height: 50px;
    }
</style>

