<template>
	<nav class="nav px-5 py-3 shadow-lg align-items-center bg-primary d-flex">
		<nuxt-link class="logo" to="/">
			Movies
		</nuxt-link>
		<div class="link  ms-auto">
			<nuxt-link class="me-4" to="/favourite">
				Favourites
			</nuxt-link>
			<nuxt-link to="/about">
				About
			</nuxt-link>
		</div>
	</nav>
</template>

<style scoped>
.logo{
	font-weight: 600;
	color: #fff;
	text-decoration: none;
	font-size: 1.25rem;
}
.link a{
	color: #fffc;
	text-decoration: none;
	transition: .25s ;
}
.link a:hover{
		color: #fff;

}
</style>