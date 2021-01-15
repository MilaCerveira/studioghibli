<template lang="html">

  <div class= "hero-bg"> 
        <section class = "top">
            <header> 
                <a href="#">Studio Ghibli</a>
            </header>
            <h1> <span> “You might be able to   </span> <span>do </span> more  than you <span>think.”</span></h1>
        </section>
       </div>

<div>
    <h2>Studio Ghibli films</h2>
    <div class="main-container">
      <movies-list :movies="movies"></movies-list>
      <movie-detail :movie="selectedMovie"></movie-detail>
    </div>
  </div>
</template>

<script>
   export default {
     data(){
       return {
         movies: [],
         selectedMovie: null,
       }
     },
    //components: {
    //"movies-list": MoviesList,
    //"movie-detail": MovieDetail
  //},

     mounted(){
       fetch('https://ghibliapi.herokuapp.com/films')
       .then(res => res.json())
       .then(movies => this.movies = movies)
     }
   }
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Montserrat:400,700&display=swap");
@import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@500&display=swap');
.hero-bg {
  background:#77AF9C
    url("https://data.whicdn.com/images/349303473/original.jpg");
  background-size: 100% 280px;
  color: white;
  text-align: center;
  padding-bottom: 4em;
  background-repeat: no-repeat;
  background-attachment: fixed;
}

header {
  padding: 1em 0;
}

.hero-bg a {
  color: white;
  text-decoration: none;
  font-weight: bold;
  font-size: 2rem;
  font-family: 'Dancing Script', cursive;
}

section {
  margin: 0 1em;
}

h1 {
  font-size: 2.5rem;
  margin: 2em 0 1.2em;
}

h1 span {
  text-transform: uppercase;
  display: block;
  font-size: 1.4rem;
  position: relative;
  z-index: 1;
}

img {
  width: 100%;
}

h1 span::before {
  content: " ";
  position: absolute;
  width: 3em;
  background: #A0D2DB;
  height: 0.4em;
  bottom: 0;
  z-index: -1;
  margin-left: -0.3em;
}

.hero-bg p {
  font-weight: bold;
  margin: 0 1em 3em;
}

.main-container {
    display: flex;
    justify-content: space-between;
    width: 80%;
    margin: 0 auto;
  }


</style>
