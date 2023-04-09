<template>
  <div class="container">
    <h1 class="text-center">Students List</h1>

    <table class="table table-striped">
      <thead>
        <tr>
          <th>Student Id</th>
          <th>Student First Name</th>
          <th>Student Last</th>
          <th>Student Email</th>
          <th>Student Phone</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="Student in Students" v-bind:key="Student.id">
          <td>{{ Student.id }}</td>
          <td>{{ Student.firstName }}</td>
          <td>{{ Student.lastName }}</td>
          <td>{{ Student.email }}</td>
          <td>{{ Student.phone }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import StudentService from "../services/StudentService";

export default {
  name: "Students",
  data() {
    return {
      Students: [],
    };
  },
  methods: {
    getStudents() {
      StudentService.getStudents().then((response) => {
        this.Students = response.data;
      });
    },
  },
  created() {
    this.getStudents();
  },
};
</script>