<template>
    <section class="contact-wrap">
  <form @submit="onSubmit" class="contact-form">
    <div class="col-sm-6">
      <div class="input-block">
        <input placeholder="Book Title" name="title" type="text" v-model="title" class="form-control">
      </div>
    </div>
    <div class="col-sm-6">
      <div class="input-block">
        <input placeholder="Author" name="Author" type="text" v-model="Author" class="form-control">
      </div>
    </div>
    <div class="col-sm-12">
      <div class="input-block">
        <input placeholder="Genre" name="Genre" type="text" v-model="Genre" class="form-control">
      </div>
    </div>
    <div class="col-sm-12">
      <div class="input-block">
        <input placeholder="ReleaseDate" name="ReleaseDate" type="text" v-model="ReleaseDate" class="form-control">
      </div>
    </div>

      <button  type="submit">add book</button>
  </form>
</section>
</template>

<script>
export default{
    name:'AddBook',
    data(){
        return{
            title: '',
            Author:'',
            Genre:'',
            ReleaseDate:'',
        }
    },
    methods:{
        onSubmit(e){
            e.preventDefault()

            if(!this.title){
                alert('Please add book title')
                return
            }
            const newBook = {
                id: Math.floor(Math.random()* 1000),
                title:this.title,
                Author:this.Author,
                Genre:this.Genre,
                ReleaseDate:this.ReleaseDate
            }
            this.$emit('add-book',newBook)

            this.title=''
            this.Author=''
            this.Genre=''
            this.ReleaseDate=''
        }
    }

}
</script>


<style scoped>

.contact-form{
    margin-top: 30px;
}
.textarea{
    height: auto;
}
.form-control{
    height: auto;
    resize: none;
}
.input-block{
    background-color: white;
    border: solid 1px green;
    width: 100%;
    height: 60px;
    padding: 25px;
    position: relative;
    margin-bottom: 20px;
}

label{
    position: absolute;
    left: 25px;
    top: 25px;
    display: block;
    margin: 0;
    font-weight: 300;
    z-index: 1;
    color: green;
    font-size: 18px;
    line-height: 10px;
}
.form-control{
    background-color: transparent;
    padding: 0;
    border: none;
    height: auto;
    position: relative;
    z-index: 2;
    font-size: 18px;
}

button{
    background-color: green;
    color: darken( 10%);
    font-size: 26px;
    text-transform: uppercase;
    font-weight: 700;
    text-align: center;
    border-radius:2px;
    padding: 0 60px;
    height: 60px;
    border: none;
    width: 100%;
}


@media (min-width: 768px) { 
  .contact-wrap{
    width: 60%;
    margin: auto;
  }
}

</style>