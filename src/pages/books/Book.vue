<template>
    <div>
      <div :key='book.id' v-for="book in books">{{book.title}}</div>
    </div>
</template>


<script>
import {get} from '@/util'

export default {
  data(){
    return {
      books:[]
    }
  },
  methods:{
    async getList(){
      const books = await get('/weapp/booklist')
      this.books = books.list
    }
  },
  mounted(){
    this.getList()
  }

}
</script>

<style>

</style>
