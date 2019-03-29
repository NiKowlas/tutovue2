<template>
  <div id="app">
    <img src="./assets/logo.png">

    
  <carousel>
    
    <carousel-slide v-for="n in slides" :index="n-1" :key="n">
      <img :src="'https://picsum.photos/1280/720/?'+n" width="100%">
    </carousel-slide>
  </carousel>
  <button @click="addSlide">Ajouter un Slide</button>
  <button @click="removeSlide">Supprimer un Slide</button>
    <todos v-model="todos"></todos>

    
    <button @click= "addTodo">Ajouter une tâche</button>
    
    <router-view></router-view>
  </div>
</template>

<script>
import Todos from './components/Todos'
import CarouselSlide from './components/carousel/CarouselSlide'
import Carousel from './components/carousel/Carousel'
export default {
  name: 'App',
  components: {
    Todos, Carousel, CarouselSlide
  },
  data () {
    return {
      slides: 5,
      todos: [{
        name: 'Demo',
        completed: true
      }]
    }
  },
  methods: {
    addTodo() {
      this.todos.push({
        name:'test',
        completed: false
      })
      
    },
    addSlide() {
      this.slides++
    },
    removeSlide() {
      this.slides--
    }
  }
}
</script>

<style>


#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
