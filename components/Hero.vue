<template>
  <div class="wrapper">
	  <div class="container">
		  	<div class="col-lg-6 mx-auto text-center py-4">
				  <h1 class="text-center">Movies</h1>
				  <p class="small text-muted">
					  Search and list favourite your movies.
				  </p>
				<div class="form-search">
				  <input type="text" placeholder="Search by IMDB Id or Title" class="form-control px-5 form-control-lg rounded-pill">
					<button class="btn btn-lg">
						<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-search" viewBox="0 0 16 16">
							<path d="M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001c.03.04.062.078.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1.007 1.007 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0z"/>
						</svg>
					</button>
				</div>
			</div>
	  </div>
  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
.form-search{
	position: relative;

}

.btn{
	position: absolute;
	right: .45rem;
	top: -2px;
}
</style>