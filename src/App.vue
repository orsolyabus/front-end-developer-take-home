<template>
  <div id="app" class="container">
    <div class="row">
      <div class="col-12 my-5 p-0">
        <h1>Fleet Assets</h1>
      </div>
      <Vehicles :vehicleList="vehicles" @remove="handleDelete"/>
    </div>
    <VehicleForm/>
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

      form: {
        year: "",
        make: "",
        model: "",
        colour: ""
      },

      errors: []
    };
  },

  methods: {
    resetFrom() {
      console.log("resetting form");
      this.form.year = null;
      this.form.make = null;
      this.form.model = null;
      this.form.colour = null;
    },
    create() {
      const index = Object.keys(this.vehicles).length + 1;
      this.errors = [];
      const formFields = { ...this.form };
      if (!formFields.year) this.errors.push("year");
      if (!formFields.make) this.errors.push("make");
      if (!formFields.model) this.errors.push("model");
      if (!formFields.colour) this.errors.push("colour");
      if (!this.errors.length) {
        this.$set(this.vehicles, index, formFields);
        this.resetFrom();
      } else {
        alert("vehicle needs " + this.errors.join(", "));
      }
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
