<template>
  <form class="mt-4">
    <div class="row">
      <div class="col">
        <input type="text" class="form-control" placeholder="Year" v-model="form.year">
      </div>
      <div class="col">
        <input type="text" class="form-control" placeholder="Make" v-model="form.make">
      </div>
      <div class="col">
        <input type="text" class="form-control" placeholder="Model" v-model="form.model">
      </div>
      <div class="col">
        <input type="text" class="form-control" placeholder="Colour" v-model="form.colour">
      </div>
      <div class="col">
        <button type="button" class="btn btn-primary mx-2" @click="create">Create</button>
        <button type="button" class="btn btn-danger mx-2" @click="resetFrom">Reset</button>
      </div>
    </div>
  </form>
</template>

<script>
export default {
  name: "vehicleForm",

  data() {
    return {
      form: {
        year: "",
        make: "",
        model: "",
        colour: "",
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
      this.errors = [];
      const formFields = { ...this.form };
      if (!formFields.year) this.errors.push("year");
      if (!formFields.make) this.errors.push("make");
      if (!formFields.model) this.errors.push("model");
      if (!formFields.colour) this.errors.push("colour");
      if (!this.errors.length) {
        this.$emit("addVehicle", formFields);
        this.resetFrom();
      } else {
        alert("vehicle needs " + this.errors.join(", "));
      }
    }
  }
};
</script>
