<template>
    <div>
      <Card :key='book.id' v-for="book in books" :book='book'></Card>
    </div>
</template>


<script>

import {get} from '@/util'
import Card from '@/components/Card'

export default {
  components:{
    Card
  },
  data(){
    return {
      books:[]
    }
  },
  methods:{
    async getList(){
      wx.showNavigationBarLoading()
      const books = await get('/weapp/booklist')
      this.books = books.list
      wx.stopPullDownRefresh()
      wx.hideNavigationBarLoading()  
    }
  },
  onPullDownRefresh(){
    this.getList()
  },
  mounted(){
    this.getList()
  }

}
</script>

<style>

</style>
