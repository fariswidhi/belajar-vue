<template>
    <div id="employee" class="container">
        <table class="table">
            <thead>
                    <th>Name</th>
                    <th>Email</th>
            </thead>
            <tbody>
                <tr v-for="employee in employees" :key="employee.id">
                    <td>{{ employee.name}}</td>
                    <td>{{ employee.email }}</td>
                </tr>
            </tbody>
        </table>
    </div>    
</template>

<script>
export default {
    name: 'employee',
    props:{
        employees: Array,
    }
}
</script>

<style>
.container{
    width: 80%;
    margin: 0 auto;
    float: left;
}
.table{
    width: 100%;
}
.table thead th{
    text-align: center;
}

</style>
