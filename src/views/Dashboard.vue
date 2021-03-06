<template>
  <div>
    <h1>Dashboard</h1>
    <v-data-table
      :headers="headers"
      :items="desserts"
      :items-per-page="5"
      class="elevation-1"
      @click:row="selectRow"
    ></v-data-table>

    <v-snackbar v-model="snackbar">
      Name: {{ employeeSelected.name }} | Title: {{ employeeSelected.title }}

      <template v-slot:action="{ attrs }">
        <v-btn color="pink" text v-bind="attrs" @click="snackbar = false">
          Close
        </v-btn>
      </template>
    </v-snackbar>
  </div>
</template>

<script>
import employees from "../data/employees.json";
export default {
  data() {
    return {
      employeeSelected: {
        name: "",
        title: "",
      },
      snackbar: false,
      headers: [
        { text: "Employee ID", value: "id" },
        { text: "Name", value: "name" },
        { text: "Salary", value: "salary" },
        { text: "Title", value: "title" },
      ],
      desserts: employees,
    };
  },
  methods: {
    selectRow(event) {
      this.snackbar = true;
      this.employeeSelected.name = event.name;
      this.employeeSelected.title = event.title;
    },
  },
};
</script>

<style lang="scss" scoped></style>
