<template>
	<div>
		<form class="form-inline mt-3" @submit.prevent="search">
			<div class="form-group mr-3">
				<input type="text" name="q" class="form-control" v-model.trim="q" placeholder="Buscar">
			</div>
			<div v-show="searching" class="loading">Buscando</div>
		</form>
		<p class="text-danger small" v-show="error">
			Debe escribir al menos 3 caracteres
		</p>
	</div>
</template>

<script>
export default {
	name: 'search-form',
	props: ['searching'],
	data() {
		return {
			q: '',
			error: false
		}
	},
	methods: {
		search() {
			if (!this.searching) {
				if (this.q.length >= 3) {
					this.error = false
					this.$emit('search', this.q)
				}
				else {
					this.error = true
				}
			}
		}
	}
}
</script>

<style>
	.loading:after {
		content: ' .';
		animation: dots 1s steps(5, end) infinite;
	}

	@keyframes dots {
		0%, 20% {
			color: rgba(0,0,0,0);
			text-shadow:
				.25em 0 0 rgba(0,0,0,0),
				.5em 0 0 rgba(0,0,0,0);
		}
		40% {
			color: black;
			text-shadow:
				.25em 0 0 rgba(0,0,0,0),
				.5em 0 0 rgba(0,0,0,0);
		}
		60% {
			text-shadow:
				.25em 0 0 black,
				.5em 0 0 rgba(0,0,0,0);
		}
		80%, 100% {
			text-shadow:
				.25em 0 0 black,
				.5em 0 0 black;
		}
	}
</style>