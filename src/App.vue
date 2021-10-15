<template>
  <div id="app">
    <div class="nav">
      <router-link to="/add-employee"> Add Employee </router-link>
      |
      <router-link to="/all-employees"> All Employees </router-link>
      |
      <router-link to="/search-employee"> Search Employee </router-link>
      |
      <router-link to="/edit-employee"> Edit Employee </router-link>
    </div>
    <router-view />
  </div>
</template>
<script>
import AddForm from "./components/AddForm.vue";
import AllEmployees from "./components/AllEmployees.vue";
import SearchForm from "./components/SearchForm.vue";
import EditForm from "./components/EditForm.vue";
export default {
  name: "App",
  components: {
    AddForm,
    AllEmployees,
    SearchForm,
    EditForm,
  },
  created: function () {
    this.employees = [];
    this.results = {};
  },
  data() {
    return {
      employees: [],
      results: {},
      edit: false,
    };
  },
  methods: {
    addEmployee(employee) {
      employee.id = this.employees.length;
      employee.show = false;
      employee.showLessIcon = "";
      this.employees.push(employee);
    },
    removeEmployee(index) {
      delete this.employees[index];
      this.employees = this.employees.filter((employee) => !!employee);
    },
    emtResults(emp) {
      this.results = emp;
      this.edit = true;
    },
    editEmployee(emp) {
      for (let i; i < this.employees.length; i++) {
        if (emp.id == this.employees[i].id) {
          this.employees[i] = emp;
        } else {
          return;
        }
      }
      this.edit = false;
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
.app {
  display: flex;
  max-width: 90%;
  padding: 5%;
  margin: 0 2.5%;
}
#app {
  margin: 1rem 15%;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  flex-direction: column;
}
.nav {
  margin-bottom: 1rem;
}
</style>
