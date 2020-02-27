
<template>
	<div id="app">


		<div @click="function(e){ mostrar('1234', e) }" id="1234" class="container">

			<h3 class="titulo">Título 1</h3>

			<transition name="fade">
				<div v-if="id == '1234'">
					<Componente01/>
				</div>
			</transition>
		</div>


		
		<div @click="function(e){ mostrar('5678', e) }" id="4567" class="container">

			<h3 class="titulo">Título 2</h3>

			<transition name="fade">
				<div v-if="id == '5678'">
					<Componente02/>
				</div>
			</transition>
		</div>
		

	</div>
</template>




<script>
	import Componente01 from './components/componente-01.vue'
	import Componente02 from './components/componente-02.vue'

	export default {

		name: 'App',
		components: {
			Componente01,
			Componente02
		},

		data()
		{
			return{
				id: 'vacio',
				id_borrar: null
			}
		},

		methods:{
			mostrar(id, e)
			{
				var contenedores = document.getElementsByClassName('container')

				for(let contenedor of contenedores)
				{
					contenedor.style.height = '30px' // Cerrar todos los contenedores
					contenedor.children[0].style.color = "#333"
				}


				var capa = e.currentTarget // Guardar elemento para que lo reconozca más abajo
				
				if(e.currentTarget.offsetHeight == 30)
				{
					this.id = id // Asignar al data() el id de la capa pulsada
					
					setTimeout(function() // Retrasamos la apertura para darle tiempo a renderizar el contenido
					{
						capa.style.height = capa.children[1].children[0].offsetHeight + 30 + 'px' // Abrir contenedor
						capa.children[0].style.color = "royalblue"
					}, 10)
				}
				else
				{
					capa.style.height = '30px' // Cerrar contenedor pulsado
				}
			}
		}
	}
</script>


<style>
	@import './assets/css/styles.css'
</style>