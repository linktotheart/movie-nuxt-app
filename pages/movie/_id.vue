<template>
	<div class="container">
		<!-- {{movie}} -->
		<h2 class="text-center mb-5 mt-4 ">{{movie.Title}}</h2>
        
          <div class="row justify-content-center ">
              <div class="col col-lg-4">
                <figure class="mb-md-4 mb-lg-0 ">
                    <img :src="movie.Poster">
                </figure>
				 
              </div>
              <div class="col col-lg-5 mt-4">
				   <p class="text-white mb-4">
					{{movie.Plot}}
					</p>
                  <!-- <h4 class="title h5 mb-4">Movie details</h4> -->
				  <ul class="list-group list-group">
					  <li class="list-group-item">
                  <strong>Genre:</strong> {{movie.Genre}} 
						  
					  </li>
					  <li class="list-group-item">
                  <strong>Language:</strong> {{movie.Language}} 

					  </li>
					  <li class="list-group-item">
                  <strong>Country:</strong> {{movie.Country}} 

					  </li>
					  <li class="list-group-item">
                  <strong>Awards:</strong> {{movie.Awards}} 

					  </li>
					  <li class="list-group-item">
                  <strong>Runtime:</strong> {{movie.Runtime}} 

					  </li>
					  <li class="list-group-item">
                  <strong>Released:</strong> {{movie.Released}} 

					  </li>
					  <li class="list-group-item">
                  <strong>Rated:</strong> {{movie.Rated}} 

					  </li>
					  <li class="list-group-item">
                  <!-- <strong>Writer:</strong> {{movies.Writer}}  -->

					  </li>
				  </ul>

				  <button @click="$router.push('/')" class="btn btn-primary">
					  Go Back 
				  </button>
              </div>
          </div>
	</div>
</template>

<script>
import axios from "axios";

export default {
	asyncData({ params }) {
		return axios
			.get(
				`http://www.omdbapi.com/?i=${params.id}&apikey=17412e4a`
			)
			.then(res => {
				console.log( res.data );
				return { movie: res.data };
				// this.movie = res.data
			});
	},
	data() {
		return{
			movie: null
		}
	}


};
</script>

<style scoped>
strong{
	margin-right: 1rem;
}
</style>