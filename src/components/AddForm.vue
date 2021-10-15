<template>
  <div>
    <div class="add-form__container">
      <h3>Add Employee</h3>
      <div class="add-form__inputs">
        <div>
          <span>Name: </span> <input v-model="employee.name" type="text" />
        </div>
        <div>
          <span>Job: </span> <input v-model="employee.job" type="text" />
        </div>
        <div>
          <span>Passport: </span>
          <input v-model="employee.password" type="text" />
        </div>
        <div>
          <span>Country: </span>
          <input v-model="employee.country" type="text" />
        </div>
        <div>
          <router-link to="/page">Page</router-link>

          <button @click="emitAddEmployee">Add</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AddForm",
  props: ["employees"],
  created: function () {
    this.employee = {};
  },
  data() {
    return {
      employee: {},
    };
  },
  methods: {
    emitAddEmployee() {
      if (this.areInputsValid()) {
        this.$emit("addEmp", this.employee);
        this.employee = {};
      }
    },
    areInputsValid() {
      if (
        !this.employee.name ||
        !this.employee.password ||
        !this.employee.job ||
        !this.employee.country
      ) {
        alert("Fill all inputs");
        return false;
      }
      return true;
    },
  },
};
</script>

<style scoped>
.add-form__container {
  display: flex;
  flex-direction: column;
  background: teal;
  padding: 1rem;
}

.add-form__container h3 {
  color: #fff;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  font-weight: 100;
  text-align: center;
  padding-bottom: 1rem;
  border-bottom: 1px dashed #fff;
}
.add-form__inputs div {
  display: flex;
  align-items: left;
  flex-direction: column;
}
.add-form__inputs div span {
  margin-top: 0.5rem;
  margin-bottom: 0.5rem;
  color: #fff;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  font-weight: 100;
}

.add-form__inputs button {
  margin-top: 1rem;
  border: 0.5px solid #fff;
  padding: 0.5rem 1rem 0.5rem 1rem;
  background: #fff;
  color: teal;
  cursor: pointer;
  transition: 0.5s ease-in-out;
}
.add-form__inputs button:hover {
  background: teal;
  color: #fff;
}
.add-form__inputs input {
  height: 2rem;
  font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
    "Lucida Sans", Arial, sans-serif;
  color: teal;
  padding-left: 1rem;
  font-size: 1rem;
  outline: none;
  border: none;
}
</style>