<template>
  <div class="search-form__container">
    <h3>Search Employees</h3>
    <div class="search-form__inputs">
      <input type="text" v-model="searchInput" @keyup="searchEmployee" />
      <button @click="clearInput" class="remove-btn">X</button>
    </div>
    <div class="results" v-for="(employee, index) in result" :key="index">
      <p ref="resultsName" @click.prevent="editEmployee(employee)">
        {{ this.result[index].name }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "SearchForm",
  props: ["employees"],
  data() {
    return {
      searchInput: "",
      result: [],
      resultsName: "",
    };
  },
  methods: {
    searchEmployee() {
      this.result = [];
      if (this.searchInput == "") {
        this.result = [];
        return;
      }

      for (let i = 0; i < this.employees.length; i++) {
        if (
          this.employees[i].name
            .toLowerCase()
            .includes(this.searchInput.toLowerCase())
        ) {
          this.result.push(this.employees[i]);
        }
      }
    },
    clearInput() {
      this.searchInput = "";
      this.result = [];
    },
    editEmployee(emp) {
      this.$emit("emtResults", emp);
      this.searchInput = "";
      this.result = [];
    },
  },
};
</script>

<style scoped>
input {
  height: 2rem;
  font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
    "Lucida Sans", Arial, sans-serif;
  color: teal;
  padding-left: 1rem;
  font-size: 1rem;
  outline: none;
  border: none;
}
p {
  color: #fff;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  font-weight: 100;
  border: 1px dashed #fff;
  padding: 5px;
  cursor: pointer;
  margin-top: 1rem;
}
.search-form__container {
  display: flex;
  flex-direction: column;
  background: teal;
  padding: 1rem;
  margin-left: 1rem;
}

.search-form__container h3 {
  color: #fff;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  font-weight: 100;
  text-align: center;
  padding-bottom: 1rem;
  border-bottom: 1px dashed #fff;
}
.search-form__inputs {
  margin-top: 1rem;
  display: flex;
  align-items: center;
}

.remove-btn {
  border: none;
  cursor: pointer;
  transition: 0.5s ease-in;
  border-radius: 50px;
  padding: 5px 6px;
  font-size: 10px;
  margin-left: 1rem;
  position: relative;
  left: -2.5rem;
  color: #fff;
  background: teal;
  border: 1px solid teal;
}

.remove-btn:hover {
  color: teal;
  background: #fff;
  border-color: teal;
}
.results {
  display: flex;
  flex-direction: column;
  max-width: 195px;
}
</style>