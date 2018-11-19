<template>
	<div class="card text-white bg-dark">
		<div class="card-body">
		  <h5 class="card-title">{{ repository.name }}</h5>
		  <h6 class="card-subtitle mb-1 text-muted">local</h6>
		</div>
	</div>
</template>

<script>
	export default {
		name: 'local-repo',
		props: ['repository']
	}
</script>