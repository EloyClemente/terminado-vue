
<template>
	<div id="app">


		<div @click="function(e){ mostrar('1234', e) }" class="container">
			<h3 class="titulo" :class="{titulo_color: id == '1234'}">Título 1</h3>
			<transition name="fade">
				<div v-if="id == '1234'">
					<Componente01/>
				</div>
			</transition>
		</div>


		
		<div @click="function(e){ mostrar('5678', e) }" class="container">
			<h3 class="titulo" :class="{titulo_color: id == '5678'}">Título 2</h3>
			<transition name="fade">
				<div v-if="id == '5678'">
					<Componente02/>
				</div>
			</transition>
		</div>



		<div @click="function(e){ mostrar('9876', e) }" class="container">
			<h3 class="titulo" :class="{titulo_color: id == '9876'}">Título 3</h3>
			<transition name="fade">
				<div v-if="id == '9876'">
					<Componente03/>
				</div>
			</transition>
		</div>



		<div @click="function(e){ mostrar('5432', e) }" class="container">
			<h3 class="titulo" :class="{titulo_color: id == '5432'}">Título 4</h3>
			<transition name="fade">
				<div v-if="id == '5432'">
					<Componente04/>
				</div>
			</transition>
		</div>
		

	</div>
</template>




<script>
	import Componente01 from './components/componente-01.vue'
	import Componente02 from './components/componente-02.vue'
	import Componente03 from './components/componente-03.vue'
	import Componente04 from './components/componente-04.vue'

	export default {

		name: 'App',
		components: {
			Componente01,
			Componente02,
			Componente03,
			Componente04
		},

		data()
		{
			return{
				id: null
			}
		},

		methods:{
			mostrar(id, e)
			{
				var contenedores = document.getElementsByClassName('container') // Obtener todas las lecciones


				for(let contenedor of contenedores)
				{
					contenedor.style.height = '30px' // Cerrar todos los contenedores
				}


				var capa = e.currentTarget // Guardar la capa pulsada para que la reconozca más abajo
				
				
				if(e.currentTarget.offsetHeight == 30) // Verificamos que el contenedor está cerrado
				{
					this.id = id // Asignar al data() el id de la capa pulsada
					
					setTimeout(function() // Retrasamos la apertura para darle tiempo a renderizar el contenido
					{
						capa.style.height = capa.children[1].children[0].offsetHeight + 30 + 'px' // Abrir contenedor
					}, 10)
				}
				else
				{
					capa.style.height = '30px' // Cerrar contenedor pulsado
					this.id = null
				}
			}
		}
	}
</script>



<style>
	
	@import './assets/css/styles.css'
</style>