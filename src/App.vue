<template>
  <div id="app">
    <vue-city-auto data="https://api-adresse.data.gouv.fr/search/?q="
              :multiple="true"
              data_to_get="city"
              result_property="features"
              input_class="form-control"
              size_font="1"
              label="city">
    </vue-city-auto>
  </div>
</template>

<script>
import VueCityAuto from './components/VueCityAuto.vue'

export default {
  name: 'app',
  components: {
    'vue-city-auto' : VueCityAuto
  }
}
</script>

<style>
#app {
  font-family: inherit;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
