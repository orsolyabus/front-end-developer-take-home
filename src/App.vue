<template>
  <div id="app" class="container">
    <div class="row">
      <div class="col-12 my-5 p-0">
        <h1>Fleet Assets</h1>
      </div>
      <Vehicles :vehicleList="vehicles" @remove="handleDelete"/>
    </div>
    <VehicleForm @addVehicle="create"/>
  </div>
</template>

<script>
import Vehicles from "./Vehicles.vue";
import VehicleForm from "./VehicleForm.vue";
export default {
  name: "app",
  components: {
    Vehicles,
    VehicleForm
  },
  data() {
    return {
      vehicles: {
        1: {
          year: "2018",
          make: "Ford",
          model: "Econoline",
          colour: "White"
        },

        2: {
          year: "2017",
          make: "Mercedes",
          model: "Sprinter",
          colour: "Black"
        }
      },
    };
  },

  methods: {
  
    create(formFields) {
      const index = Object.keys(this.vehicles).length + 1;
        this.$set(this.vehicles, index, formFields);
    },
    handleDelete(index) {
      this.$delete(this.vehicles, index);
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
