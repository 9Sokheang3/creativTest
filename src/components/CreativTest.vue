<template>
  <div class="container p-5">
    <div>
      <form action="#">
        <div class="form-group">
          <input type="number" name="employeeID" id="employeeID" placeholder="Enter ID..." class="form-control" v-model="id">
        </div>
        <div class="form-group">
          <input type="text" name="employeeFirstName" id="employeeFirstName" placeholder="Enter first name..." class="form-control" v-model="firstname">
        </div>
        <div class="form-group">
          <input type="text" name="employeeLastName" id="employeeLastName" placeholder="Enter last name..." class="form-control" v-model="lastname">
        </div>
        <div class="form-group">
          <input type="text" name="employeeGender" id="employeeGender" placeholder="Enter gender..." class="form-control" v-model="gender">
        </div>
        <button type="button" class="btn btn-primary m-5" @click="saveEmployee()">Save employee</button>
      </form>
    </div>
    <table class="table mb-5" style="width:100%; border-collapse: collapse;">
      <thead class="font-weight-bold">
        <tr>
          <th>id</th>
          <th>firstName</th>
          <th>lastname</th>
          <th>gender</th>
          <th>salary</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(employee, index) in employees" :key="index" class="border-collapse p-5">
          <td>{{ employee.id }}</td>
          <td>{{ employee.firstname }}</td>
          <td>{{ employee.lastname }}</td>
          <td>{{ employee.gender }}</td>
          <td>
            <span v-if="employee.gender.toLowerCase() === 'male'">500$</span>
            <span v-else>450$</span>
          </td>
        </tr>
      </tbody>
    </table>
    <div>
      <h1>{{ total }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DemoTest',
  data() {
    return {
      id: null,
      firstname: null,
      lastname: null,
      gender: null,
      employees: [{
        id: 1,
        firstname: 'John',
        lastname: 'Doe',
        gender: "Male",
      },{
        id: 2,
        firstname: 'kaka',
        lastname: 'vich',
        gender: "Female",
      },{
        id: 3,
        firstname: 'yaya',
        lastname: 'dom',
        gender: "Male",
      },{
        id: 4,
        firstname: 'jojo',
        lastname: 'nasa',
        gender: "Female",
      }],
    };
  },
  methods: {
    saveEmployee() {
      this.employees.push({
        id: this.id,
        firstname: this.firstname,
        lastname: this.lastname,
        gender: this.gender,
      });
    },
  },
  computed: {
    total() {
      return this.employees.length;
    },
  },
};
</script>

<style>
input{
  margin: 2px;
}
</style>
