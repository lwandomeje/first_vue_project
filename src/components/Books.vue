<template>
       
    <div :key="book.id" v-for="book in books">

     <table>
    	<thead>
		    <tr>
			    <th>ID</th>
			    <th>Title</th>
			    <th>Author</th>
			    <th>Genre</th>
                <th>ReleaseDate</th>
                <th>Delete</th>
		    </tr>
	    </thead>
                <tr> 
                    <td>{{ book.id}}</td>
                    <td>{{ book.title}}</td>
                    <td>{{ book.Author}}</td>
                    <td>{{ book.Genre}}</td>
                    <td>{{ book.ReleaseDate}}</td>
                    <td><i @click="onDelete(book.id)" class="fas fa-times"></i></td>
                </tr>
        </table> 

    </div>
</template>

<script>
    export default{
        name:'Books',
        props: {
            books: Array
        },
        methods:{
            onDelete(id){
                this.$emit('delete-book', id)
            },
        },
        emits: ['delete-book']
    }
</script>

<style scoped>
.fas{
  color:red  
}
body {
  	font-family: 'Poppins', sans-serif;
  display: grid;
  padding: 100px;
  color: #4f546c;
  font-size: 0.9rem;
}
.table-out{
  border-collapse: collapse;
  box-shadow: 0 5px 10px #e1e5ee;
  background-color: white;
  text-align: left;
  overflow: hidden;
  width: 100%;

}
table {
  border-collapse: collapse;
  box-shadow: 0 5px 10px #e1e5ee;
  background-color: white;
  text-align: left;
  overflow: hidden;
  width: 100%;
}
  thead {
    box-shadow: 0 5px 10px #e1e5ee;
  }

  th {
    padding: 1rem 2rem;
    text-transform: uppercase;
    letter-spacing: 0.1rem;
    font-size: 0.7rem;
    font-weight: 900;
  }

  td {
    padding: 1rem 2rem;
  }

</style>