<template>
  <div class="card">
    <img :src="image" class="card-img-top" alt="..." />
    <h2 class="card-header" v-if="!stolen">{{ petName }}</h2>
    <h2 class="card-header" v-else>{{ petName }} have been stolen!</h2>
    <div class="card-body" v-if="!stolen">
      <h5 class="card-title">
        {{ description }}
      </h5>
      <p>Cuteness Level: {{ value }}</p>
      <vue-slider v-model="value" />
    </div>
    <button
      type="button"
      class="btn btn-danger"
      id="steal"
      @click="stealIt"
      v-if="!stolen"
    >
      Steal
    </button>
    <button
      type="button"
      class="btn btn-success"
      id="steal"
      @click="stealIt"
      v-else
    >
      Return
    </button>
  </div>
</template>

<script>
  import VueSlider from 'vue-slider-component'
  import 'vue-slider-component/theme/antd.css'
  export default {
    name: 'NavBar',
    components: {
      VueSlider,
    },
    props: {
      imgUrl: String,
      description: String,
      petName: String,
    },
    data() {
      return {
        value: 0,
        stolen: false,
        image: this.imgUrl,
        imageStolen:
          'https://images.pexels.com/photos/9428571/pexels-photo-9428571.jpeg?cs=srgb&dl=pexels-katya-wolf-9428571.jpg&fm=jpg',
      }
    },
    methods: {
      stealIt: function () {
        this.stolen = !this.stolen
        if (this.stolen) {
          this.image = this.imageStolen
        } else {
          this.image = this.imgUrl
        }
      },
    },
  }
</script>

<style>
  .card {
    margin: 0;
  }

  .card-img-top {
    height: 50vh;
    object-fit: cover;
  }

  #steal {
    margin: 0;
  }
</style>
