<template>
  <div class="container">
    <Header />
    <AddBook @add-book="addbook" />
    <Books @delete-book="deleteBook" :books="books" />

  </div>
</template>

<script>
import Header from './components/Header'
import Books from './components/Books'
import AddBook from './components/AddBook'


export default {
  name: 'App',
  components: {
    Header,
    Books,
    AddBook
  },
    data(){
      return{
        books: [],
    }
  },
  methods:{

    async addbook(book){
      const res = await fetch('http://localhost:5000/books',{
        method:'POST',
        headers:{
          'Content-type':'application/json',
        },
        body:JSON.stringify(book),
      })
      const data = await res.json()
      this.books = [...this.books,data]
    },

    async deleteBook(id){
      if (confirm('This book will be deleted')){
        const res = await fetch(`http://localhost:5000/books/${id}`,
        {
          method:'DELETE'
        })
        res.status === 200 ? (this.books = this.books.filter((book) => book.id !== id))
        : alert('error deleting')
        
      }
    },


    async fetchBooks(){
      const res = await fetch('http://localhost:5000/books')
      const data = await res.json()
      return data
    }
  },
  async created() {
      this.books = await this.fetchBooks()
    }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
}
.container {
  max-width: 100%;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 0px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
