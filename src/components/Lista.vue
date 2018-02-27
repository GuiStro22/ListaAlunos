<template>
	<div id="app">
		<header class="cabeçalho">
			<h1 class="titulo-lista">Lista</h1>
		</header>
		<form>
			<div>
				<label> Ordenar por: </label><br>
				<select v-model="configs.orderBy">
					<option value='name'> Nome </option>
					<option value='age'> Idade </option>
				</select>
			</div>
			<div>
				<label> Ordem: </label><br>
				<select  v-model="configs.order">
					<option value="asc"> Crescente </option>
     				<option value="desc"> Decrescente </option>
				</select>
			</div>
			<div>
				<label> Filtrar </label>
				<input type="text" class="form-control" placeholder="Filtrar repo por nome" v-model="configs.filter">
			</div>
		</form>
		<ListaAlunos :list="list"></ListaAlunos>
	</div>
</template>
<script>
	import _ from 'lodash'
	import ListaAlunos from './ListaAlunos.vue'

	export default {
		name: 'Lista',
		data(){
			return{
				configs: {
			    orderBy: 'name',
			    order: 'desc',
			    filter: ''
			    },
				alunos:[
					{
						name: 'Guilherme',
						age: '17'
					},
					{
						name: 'André',
						age: '23'
					},
					{
						name: 'Ricardo',
						age: '32'
					}
				]
			}
		},
		computed: {
			list () {
				const filter = this.configs.filter;
      			const list = _.orderBy(this.alunos, this.configs.orderBy, this.configs.order);

			    if (_.isEmpty(filter)) {
			    return list;
			    }


				return _.filter(list, aluno => aluno.name.indexOf(filter) >= 0);
			}
		},
		components: {
			ListaAlunos
		}
	}
</script>
<style>
	#app{

	}
	.cabeçalho{

	}
	.titulo-lista{

	}
	.lista{

	}
</style>