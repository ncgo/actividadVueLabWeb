<template>
  <NavBar />
  <div class="content">
    <h1 style="color: #ff5714; text-transform: uppercase">
      Welcome to Mascotalandia
    </h1>
    <div class="container-fluid cards">
      <div class="row justify-content-center">
        <div class="col-6">
          <PetCard
            :key="pets[current].name"
            :imgUrl="pets[current].imageUrl"
            :description="pets[current].description"
            :petName="pets[current].name"
          />
        </div>
        <div class="col-2 align-self-center">
          <button
            type="button"
            class="btn btn-outline-primary"
            @click="changeCardDogs"
            v-if="current != 0"
          >
            Dogs & Puppies
          </button>
          <button
            type="button"
            class="btn"
            style="border-color: #ffb800; color: #ffb800"
            @click="changeCardCats"
            v-if="current != 1"
          >
            Cats & Kittens
          </button>
          <button
            type="button"
            class="btn"
            style="border-color: #ff5714; color: #ff5714"
            @click="changeCardOthers"
            v-if="current != 2"
          >
            Other fun animals
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import NavBar from './components/NavBar.vue'
  import PetCard from './components/PetCard.vue'

  export default {
    name: 'App',
    data() {
      return {
        current: 0,
        stolen: false,
        pets: [
          {
            name: 'Dogs & Puppies',
            imageUrl:
              'https://images.pexels.com/photos/7516509/pexels-photo-7516509.jpeg?cs=srgb&dl=pexels-kateryna-babaieva-7516509.jpg&fm=jpg',
            description: "Man's best friend",
          },
          {
            name: 'Cats & Kittens',
            imageUrl:
              'https://images.pexels.com/photos/8727896/pexels-photo-8727896.jpeg?cs=srgb&dl=pexels-archibald-marajas-8727896.jpg&fm=jpg',
            description: 'Superior beings',
          },
          {
            name: 'Birds and other oddities',
            imageUrl:
              'https://images.pexels.com/photos/56733/pexels-photo-56733.jpeg?cs=srgb&dl=pexels-caio-56733.jpg&fm=jpg',
            description: "You'll be the life of the party",
          },
        ],
      }
    },
    components: {
      NavBar,
      PetCard,
    },
    methods: {
      changeCardDogs: function () {
        this.current = 0
      },
      changeCardCats: function () {
        this.current = 1
      },
      changeCardOthers: function () {
        this.current = 2
      },
      stealPet: function () {
        this.stolen = true
      },
    },
  }
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }

  .content {
    padding: 2vw;
    text-align: center;
  }

  .cards {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-content: center;
  }

  .btn {
    margin: 2vh;
  }
</style>
