<template>
<div id="employee-form">
    <div class="full">
    <p v-if="success">
        ✅ Employee successfully added
    </p>
    <p id="error && submitting">❗Please fill out all required field</p>
            <div class="row">
                <div class="col-lg-12">
                     <form @submit.prevent="handleSubmit" class="form">
        <div class="form-group">
        <label for="name">Name</label><br>
        <input ref="first" v-model="employee.name" type="text" class="form-control"/><br/>
        </div>
        <div class="form-group">
              <label for="email" >Email</label><br>
        <input  v-model="employee.email" type="text" class="form-control">
        </div>
        <button class="btn btn-success">Save</button>
            <br>
    </form>
                </div>
            </div>
    </div>
</div>
</template>

<script>
export default {
    name:'employee-form',
    data(){
        return{
            error:false,
            submitting:false,
            success:false,
            employee:{
                name: '',
                email:''
            }
        }
    },
    computed:{
        invalidName(){
            return this.employee.name==='';
        },
        invalidEmail(){
            return this.employee.email==='';
        }
    },
    methods:{
        handleSubmit(){
            // alert("x");
            // console.log(this.employee);
            this.submitting=true;
            this.clearStatus();
            if(this.invalidName|| this.invalidEmail){

                // alert("Isi Form!");
                this.error=true;
                return;
            }
            this.$emit("add:employee",this.employee);
            this.employee ={
                name:'',
                email:''
            }
            this.$refs.first.focus();

            this.success=true;
            this.error = false;
            this.submitting=false;
        },
        clearStatus(){
            this.success=false;
            this.error=false;
        }
    }
}
</script>
