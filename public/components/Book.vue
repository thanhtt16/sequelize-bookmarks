<template>
<div>
<a v-link="{ path: '/books' }" class='btn btn-default pull-left'>Back</a>

	<div class='col-sm-6 col-sm-offset-3'>
		<h1>{{book.title}}</h1>	
	</div>
</div>
	
</template>

<script>
import routes from 'vue-router'

export default {
	name: 'book',
	components: {
		routes
	},
	data(){
		return {
			book: {}
		}
	},
	ready(){
		this.getBook()
	},
	methods: {
		getBook(){
			this.$http.get('/api/books/' + this.$route.params.id)
				.then(res => this.book = res.body)
		}
	}
}
</script>