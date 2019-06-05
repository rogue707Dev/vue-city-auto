<template>
  <div id="app">
    <vue-city data="https://api-adresse.data.gouv.fr/search/?q="
              :multiple="true"
              data_to_get="city"
              result_property="features"
              input_class="form-control"
              size_font="1"
              label="cp">
    </vue-city>
  </div>
</template>

<script>
import CityComponent from './components/CityComponent.vue'

export default {
  name: 'app',
  components: {
    'vue-city' : CityComponent
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
