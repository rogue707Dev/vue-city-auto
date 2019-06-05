<!-- Vue component -->
<template>
    <div id="app">
        <autocomplete
                :source="urlEndpoint"
                :results-property="result_property"
                @selected="addElement"
                :inputClass="input_class"
                :results-display="formatDisplay">
        </autocomplete>

        <template v-for="(value, index) in this.listShow ">
                <span class="tag dynamic" @click="removeElement(index)">{{value[1]}}  ( {{value[0]}} )
                <span class="close">
                    <img src="../assets/times-solid.svg" class="autocomplete__icon">

                </span> </span>
        </template>

        <input type="hidden" :name="label" :value="selectedData">
    </div>
</template>

<script>
    import Autocomplete from "vuejs-auto-complete";


    export default {
        name: 'vue-city',
        components: {
            Autocomplete
        },
        props: {
            data: null,
            label: null,
            input_class: null,
            result_property: null,
            data_to_get: null,
            size_font: null,
            multiple: Boolean,
        },
        data() {
            return {
                value: [],
                listShow: [],
                select: 'Appuyer sur entrée pour choisir',
                deselect: 'Appuyer sur entrée pour annuler',
                selected: "Sélectionné",
            }
        },
        mounted() {
            // console.log(this.data);
        },
        methods: {
            urlEndpoint(input) {
                return this.data + input
            },
            formatDisplay(result) {
                return result.properties.label + ', ' + result.properties.postcode
            },
            addElement(element) {
                var data_to_grab = '';
                switch (this.data_to_get) {
                    case 'postcode':
                        data_to_grab = element.selectedObject.properties.postcode;
                        break;
                    case 'address':
                        data_to_grab = element.selectedObject.properties.label;
                        break;
                    case 'name':
                        data_to_grab = element.selectedObject.properties.name;
                        break;
                    case 'city':
                        data_to_grab = element.selectedObject.properties.city;
                        break;
                    case 'citycode':
                        data_to_grab = element.selectedObject.properties.citycode;
                        break;
                    default:
                        console.log('Sorry, we are out of ' + expr + '.');
                        break;
                }

                this.listShow.push([data_to_grab,
                    element.selectedObject.properties.label]);
                this.value.push(data_to_grab)
            },
            removeElement(elementId) {
                // console.log(elementId);
                this.listShow.splice(elementId, 1);
                this.value.splice(elementId, 1);
            }
        },
        computed: {
            selectedData: function () {
                let selectedUsers = [];
                Object.keys(this.value).forEach(key => {
                    let val = this.value[key];// value of the current key
                    if (typeof (val) == 'object') {
                        Object.keys(val).forEach(key => {
                            let value = val[key];// value of the current key
                            selectedUsers.push(value);
                        });
                    } else {
                        selectedUsers.push(val);
                    }
                });
                return selectedUsers;
            },
            cssProps() {
                return {
                    '--font-size': (this.size_font) + "rem"
                }
            }
        }
    }
</script>
<style>
    .multiselect, .multiselect__input, .multiselect__single {
        font-size: var(--font-size);
    }

    #app {
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
    }

    span.tag {
        display: block;
        float: left;
        padding: 5px 9px;
        text-decoration: none;
        background: white;
        color: #aaaaaa !important;
        border: 1px solid #aaaaaa;
        margin-right: 7px;
        font-weight: 500;
        margin-bottom: 0px;
        border-radius: 10px;
    }

    span.dynamic {
        cursor: pointer;
        margin: 0.5rem;
        padding: 4px 10px;
    }

    span.dynamic:hover {
        background-color: #cb0a3c;
        color: white !important;
    }

</style>
