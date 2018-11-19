<template>
	<div class="card-columns mt-3">
		<local-repo
			v-for="repo in repositories.local" 
			:key="repo.name"
			:repository="repo" />
		<github-repo
			v-for="repo in repositories.github" 
			:key="repo.id"
			:repository="repo" />
	</div>
</template>

<script>
import LocalRepo from './LocalRepo.vue'
import GithubRepo from './GithubRepo.vue'

export default {
	name: 'repositories-list',
	props: ['repositories'],
	components: {
		LocalRepo,
		GithubRepo
	}
}
</script>