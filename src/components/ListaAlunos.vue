<template>
	<section>
		<ul class="lista">
			<li v-for="aluno in list">
				<strong>{{aluno.name}}</strong><br>
				{{aluno.age}} anos.
				
			</li>
		</ul>
	</section>
</template>
<script>
	export default{
		name: 'ListaALunos',
		props:{
			list:{
				type: Array,
				required: true
			}
		},
		data(){
			return{
				
			}
		}
	}
</script>
<style>
	
</style>