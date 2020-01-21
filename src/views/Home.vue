<template>
  <div class="home-view-container">
    <h1>ADOPT A NEW BEST FRIEND</h1>
    <br>
    No of Cats available: {{getAllCats.length}} <br>
    No of Cats available: {{getAllDogs.length}} <br>
    No of Animals Available: {{animalsCount}} <br>
    <br>
    <button @click="togglePetForm" class="btn btn-primary">Add new Pet</button>
    <br>

  <b-form @submit.prevent="handleSubmit" v-if="showPetForm">

      <b-form-group id="input-group-2" label="Pet's  Name:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="formData.name"
          required
          placeholder="Enter name"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-3" label="Species:" label-for="input-3">
        <b-form-select
          id="input-3"
          v-model="formData.species "
          :options="['cats', 'dogs']"
          required
        ></b-form-select>
      </b-form-group>

      <b-form-group id="input-group-2" label="Pet's  Age:" label-for="input-2">
        <b-form-input
          id="input-2"
          type="number"
          v-model="formData.age"
          required
          placeholder="Enter Age"
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>

  </div>
</template>

<script>
// @ is an alias to /src
/* eslint-disable */
import { mapActions, mapGetters } from 'vuex'

export default {
  name: 'home',

  data() {
  return {
    showPetForm: false,
    formData: {
      name: "",
      age: 0,
      species: null
    }
  }
},
computed: {
   ...mapGetters([
      'animalsCount',
      'getAllCats',
      'getAllDogs'
   ])
},
  methods: {
    ...mapActions([
      'addPet'
    ]),
    togglePetForm(){
      this.showPetForm = !this.showPetForm
    },
    handleSubmit() {
    const { species, age, name } = this.formData
    const payload =  {
      species,
      pet: {
        name,
        age
      }
    } 
    this.addPet(payload)

    //Resets from after submit

    this.formData = {
      name: "",
      age: 0,  
      species: null
    }
  }
    
  }
  
}
</script>
