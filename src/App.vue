

<template>
  <div id="app" class="container">
    <h1>Employees</h1>
  <div class="container">
    <div class="row">
      <div class="col-lg-12">
         <div class="card">
      <div class="card-body">

    <employee-form @add:employee="addEmployee"/>
    <br>
  <employee v-bind:employees="employees"/>
      </div>
    </div>
      </div>
    </div>
  </div>
  </div>
</template>

<script>
import Employee from './components/Employee.vue';
import EmployeeForm from './components/Form.vue';
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

export default {
  name: 'app',
  components: {
    Employee,
    EmployeeForm
  },
  data(){
    return{
      employees:[
      ]
    }
  },
  methods:{
        addEmployee(employee){
            console.log(employee);
            const lastId = this.employees.length >0  ? this.employees[this.employees.length-1].id:0;
            const id = lastId+1;
            const newEmployee = {...employee,id};
          console.log("XXX");
          console.log(newEmployee);
            this.employees =[...this.employees,newEmployee];

        }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button{
  background: #009435;
  border: 1px solid #009435;
}

.small-container{
  margin: 0 auto;
}

</style>
