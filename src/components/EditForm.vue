<template>
  <div>
    <div class="edit-form__container">
      <h3>Edit Employee</h3>
      <div class="edit-form__inputs">
        <div>
          <span>Name: </span>
          <input type="text" v-model="this.editedEmployee.name" />
        </div>
        <div>
          <span>Job: </span>
          <input type="text" v-model="this.editedEmployee.job" />
        </div>
        <div>
          <span>Passport: </span>
          <input type="text" v-model="this.editedEmployee.password" />
        </div>
        <div>
          <span>Country: </span>
          <input type="text" v-model="this.editedEmployee.country" />
        </div>
        <div>
          <button @click="save">Save</button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "EditForm",
  props: ["results"],
  data() {
    return {
      editedEmployee: {},
    };
  },
  created: function () {
    this.editedEmployee = this.results;
    console.log(this.editedEmployee);
  },
  methods: {
    save() {
      this.$emit("editEmp", this.editedEmployee);
    },
  },
};
</script>

<style scoped>
.edit-form__container {
  display: flex;
  flex-direction: column;
  background: teal;
  padding: 1rem;
  margin-left: 1rem;
}

.edit-form__container h3 {
  color: #fff;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  font-weight: 100;
  text-align: center;
  padding-bottom: 1rem;
  border-bottom: 1px dashed #fff;
}
.edit-form__inputs div {
  display: flex;
  align-items: left;
  flex-direction: column;
}
.edit-form__inputs div span {
  margin-top: 0.5rem;
  margin-bottom: 0.5rem;
  color: #fff;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  font-weight: 100;
}

.edit-form__inputs button {
  margin-top: 1rem;
  border: 0.5px solid #fff;
  padding: 0.5rem 1rem 0.5rem 1rem;
  background: #fff;
  color: teal;
  cursor: pointer;
  transition: 0.5s ease-in-out;
}
.edit-form__inputs button:hover {
  background: teal;
  color: #fff;
}
.edit-form__inputs input {
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

