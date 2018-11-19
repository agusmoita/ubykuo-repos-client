<template>
	<div>
		<form class="form-inline mt-3" @submit.prevent="search">
			<div class="form-group mr-3">
				<input type="text" name="q" class="form-control" v-model.trim="q">
			</div>
			<button type="submit" class="btn">{{ buttonText }}</button>
		</form>
		<p class="text-danger small" v-show="error">
			Debe escribir al menos 3 caracteres
		</p>
	</div>
</template>

<script>
export default {
	name: 'search-form',
	props: ['enabled'],
	data() {
		return {
			q: '',
			error: false
		}
	},
	methods: {
		search() {
			if (this.enabled) {
				if (this.q.length >= 3) {
					this.error = false
					this.$emit('search', this.q)
				}
				else {
					this.error = true
				}
			}
		}
	},
	computed: {
    buttonText() {
      return this.enabled ? 'Buscar' : 'Buscando...'
    }
  }
}
</script>