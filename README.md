# Vue-City-Auto

Vue-City-Auto is a VueJS component of an autocomplete city input.

## Project setup
```bash
yarn install
```

In your project app.js : 

```javascript
// If not already set
import Vue from 'vue' 
import VueCity from 'vue-city'

new Vue({
  //...
  components: {
    VueCity,
  },
  //...
})
```

And in your blade template or html : 
```html
    <vue-city data="https://api-adresse.data.gouv.fr/search/?q="
              :multiple="true"
              data_to_get="city"
              result_property="features"
              input_class="form-control"
              size_font="1"
              label="city_input">
    </vue-city>
``` 

### Available props

| Prop                  | Type                        | Required | Default   | Description |
|-----------------------|-----------------------------|----------|-----------|-------------|
| multiple              | Boolean                     |          | false     | for multiple selectable adresses|
| source                | String                      |         | https://api-adresse.data.gouv.fr/search/?q=         | api url to make request to|
| result_property       | String                      |         | features | Based on the API answer object where results are stored|
| input_class          | String                       |    X     |   form-control        | Class of the input|
| size_font          | Integer                       |    X     |   1        | Font size in rem|
| label          | String                       |    X     |           | Name of your hidden input field|



### Compiles and hot-reloads for development
```
yarn run serve
```

### Compiles and minifies for production
```
yarn run build
```

### Run your tests
```
yarn run test
```

### Lints and fixes files
```
yarn run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).


##Usage



