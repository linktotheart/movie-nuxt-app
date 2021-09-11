<template>
	<div>
		<section class="main-wrap">
			<div class="container mt-5">
				<!-- /// search ui  -->

				<div class="col-lg-6 mx-auto text-center py-4">
					<h1 class="text-center">Movies</h1>
					<p class="small text-muted">
						Search and list favourite your movies.
					</p>
          
          <button v-if="favMovies.length > 0" @click="ShowFavMovies" class="btn btn-outline-primary px-5 btn-sm">
            See Favourites
          </button>

					<div class="form-search">
						<input
							type="text"
              v-model="search"
							placeholder="Search by IMDB Id or Title"
							class="form-control px-5 form-control-lg rounded-pill"
						>
						<button class="btn btn-lg"
              @click="getMovie(search)"
            >
							<svg
								xmlns="http://www.w3.org/2000/svg"
								width="16"
								height="16"
								fill="currentColor"
								class="bi bi-search"
								viewBox="0 0 16 16"
							>
								<path d="M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001c.03.04.062.078.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1.007 1.007 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0z" />
							</svg>
						</button>
					</div>
				</div>


        <!-- /// listing  -->
				<div class="row ">
					<div
						class="col-lg-3 "
						v-for="(movie, index) in movies"
						:key="index"
					>
						<div class="card mb-3">
							<div class="card-image">
								<img
									:src="movie.Poster"
									:alt="movie.Title"
								>
							</div>
							<div class="card-body">
								<h5 class="card-title">
                  
									<nuxt-link :to="'/movie/' + movie.imdbID">{{movie.Title}}</nuxt-link>
								</h5>
								<p class="subtitle">{{movie.Plot}}</p>
							</div>
							<div class="card-footer">

								<span class="badge bg-secondary"> {{movie.Year}}</span>


                <button @click="addToFav(movie.imdbID)" class="btn-sm btn btn-outline-dark">
                  <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-star-fill" viewBox="0 0 16 16">
                    <path d="M3.612 15.443c-.386.198-.824-.149-.746-.592l.83-4.73L.173 6.765c-.329-.314-.158-.888.283-.95l4.898-.696L7.538.792c.197-.39.73-.39.927 0l2.184 4.327 4.898.696c.441.062.612.636.282.95l-3.522 3.356.83 4.73c.078.443-.36.79-.746.592L8 13.187l-4.389 2.256z"/>
                  </svg>
                </button>

							</div>
						</div>
					</div>
				</div>
			</div>
		</section>

	</div>
</template>

<script>
import Header from "~/components/Header.vue";
import axios from "axios";
export default {
	components: {
		Header
	},
	data() {
    return{
      movies: [],
      search: "",
      favMovies: [],
    }
	},

	asyncData({ req, params }) {
		return axios
			.get(`http://www.omdbapi.com/?s=marvel&apikey=17412e4a&plot=short`)
			.then(res => {
				return { movies: res.data.Search };
			});
	},
	head: {
		title: "Best movie searching!"
	},

  methods: {
    async getMovie() {
      // if (this.search == "") {
      //   return alert("Enter a movie name")
      // }
      // else{
        console.log(this.search);
        this.movies = await axios
        .get(`http://www.omdbapi.com/?s=${this.search}&apikey=17412e4a&plot=short`)
        .then(res => {
          return  res.data.Search ;
        });
      // }
    },
    async ShowFavMovies(){
        console.log(this.favMovies);

       this.movies = await axios
        .get(`http://www.omdbapi.com/?s=${this.favMovies}&apikey=17412e4a&plot=short`)
        .then(res => {
          return  res.data.Search ;
        });
    },

    addToFav( id ){
      this.favMovies.push(id);
      alert("Added to Favourites")
    }
  },
};
</script>


<style scoped>
.card {
	min-height: 250px;
	height: calc(100% - 1rem);
}
.card-image {
	position: relative;
	padding-top: 100%;
	overflow: hidden;
}

.card-image img {
	position: absolute;
	top: 0;
	bottom: 0;
	left: 0;
	right: 0;
}
.card-title a{
  text-decoration: none;
  color: inherit;
}
</style>