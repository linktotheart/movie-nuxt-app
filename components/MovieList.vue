<template>
  <div class="container">
	  <div class="row">
		  <div v-for="movie in movies" :key="movie.id" class="col-md-4 col-lg-3">
			  <div class="card">
				  <div class="card-title">
					  {{movie.Title}}
				  </div>
			  </div>
		  </div>
	  </div>
  </div>
</template>

<script>
export default {
 props: [
    'movies'
  ],
}
</script>

<style>

</style>