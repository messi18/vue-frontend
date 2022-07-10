<template>
    <div class="container">
        <h1 class="text-center">Employee List</h1>    
        <table class="table table-striped">
            <thead>
                <th>Employee Id</th>
                <th>Employee First Name</th>
                <th>Employee Last Name</th>
            </thead>
            <tbody>
                <tr v-for="employee in employee_list" v-bind:key="employee.Id">
                    <td> {{employee.id}}</td>
                    <td> {{employee.firstName}}</td>
                    <td> {{employee.lastName}}</td>
                </tr>
            </tbody>
        </table>
    </div>    
</template>
<script>
    import EmployeeService from '../service/EmployeeService'
    export default {
        name:'employee_list',
        data() {
            return {
                employee_list:[]
            }
        },
        methods:{
            getEmployees() {
                EmployeeService.getEmployees().then((response) => {
                    this.employee_list = response.data;
                })
            }
        },
        created() {
            this.getEmployees()
        }
    }
</script>