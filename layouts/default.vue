<template>
  <div class="wrapper d-flex flex-column min-vh-100">
		<Header />
		<main class="flex-grow">
			<Nuxt />
		</main>
		<footer>
			<div class="text-center text-muted py-4">
				Coded by Pulkit Singh, in Nuxt.JS 
			</div>
		</footer>
  </div>
</template>

<style lang="css"	>
.wrapper{
	min-height: 100vh;
}
.flex-grow{
	flex-grow: 1;
}
</style>