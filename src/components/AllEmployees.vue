<template>
  <div class="all-employees__container">
    <h3>All Employees</h3>
    <div
      class="employee-list"
      id="employeeList"
      v-for="(emp, index) of employees"
      :key="index"
    >
      <div class="empTitle">
        <p @click="showEmpDetails(emp)">
          {{ emp.name }}
        </p>
        <br />
        <p @click="showLess(emp)">{{ emp.showLessIcon }}</p>
        <button
          class="remove-btn"
          v-bind="removeBtn"
          @click="$emit('removeEmp', index)"
        >
          X
        </button>
        <br />
      </div>

      <div v-if="!!emp.show" class="detail" id="empDetail">
        <p>
          {{ this.employees[index].job }}
        </p>
        <p>
          {{ this.employees[index].password }}
        </p>
        <p>
          {{ this.employees[index].country }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AllEmployees",
  props: ["employees"],

  data() {
    return {};
  },
  methods: {
    showEmpDetails(emp) {
      emp.showLessIcon = "^";
      emp.show = true;
    },
    showLess(emp) {
      emp.show = false;
      emp.showLessIcon = "";
    },
  },
};
</script>
<style  scoped>
.all-employees__container {
  display: flex;
  flex-direction: column;
  background: teal;
  padding: 1rem;
  margin-left: 1rem;
}

.all-employees__container h3 {
  color: #fff;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  font-weight: 100;
  text-align: center;
  padding-bottom: 1rem;
  border-bottom: 1px dashed #fff;
}
.employee-list {
  display: flex;
  flex-direction: column;
  margin-top: 1rem;
  border: 1px dashed #fff;
  padding: 0.5rem;
  cursor: pointer;
}
.employee-list p {
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  color: #fff;
}
.empTitle {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.remove-btn {
  border: none;
  padding: 5px;
  color: teal;
  border: 1px solid #fff;
  cursor: pointer;
}

.remove-btn:hover {
  color: #fff;
  background: teal;
}

#empDetail p {
  color: #fff;
}
.more-btn {
  border: 1px solid #fff;
  padding: 1px 3px 3px 3px;
  margin-top: 1rem;
  margin-left: 5rem;
  background: teal;
  color: #fff;
  cursor: pointer;
  transition: 0.5s ease-in-out;
}
.more-btn:hover {
  background: #fff;
  color: teal;
}
</style>