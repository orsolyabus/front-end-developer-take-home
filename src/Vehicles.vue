<template>
  <div class="col-12 p-0">
    <table class="table">
      <thead>
        <tr>
          <th scope="col">Year</th>
          <th scope="col">Make</th>
          <th scope="col">Model</th>
          <th scope="col">Colour</th>
          <th scope="col">Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(vehicle, index) in vehicleList" :key="index">
          <td>{{ vehicle.year }}</td>
          <td>{{ vehicle.make }}</td>
          <td>{{ vehicle.model }}</td>
          <td>{{ vehicle.colour }}</td>
          <td>
            <button
              type="button"
              class="btn btn-sm btn-outline-danger mx-2"
              @click="handleDelete(index)"
            >Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "vehicles",
  props: {vehicleList:{
      type: Object,
      required: true
  }},
  methods: {
    handleDelete(id) {
      this.$emit('remove', id);
    }
  }
};
</script>

