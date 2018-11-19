<template>
	<div class="card">
		<div class="card-body">
		  <h5 class="card-title">{{ repository.name }}</h5>
		  <h6 class="card-subtitle mb-1 text-muted">{{ repository.full_name }}</h6>
		  <p class="card-text">{{ repository.description }}</p>
		  <a :href="repository.url" class="card-link" target="_blank">
		  	Ver en GitHub
		  </a>
		</div>
	</div>
</template>

<script>
	export default {
		name: 'github-repo',
		props: ['repository']
	}
</script>