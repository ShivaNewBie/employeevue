<template>
  
              

  <form @submit='onSubmit' class="add-form">
    <div class="form-control">
      <label>Employee Name</label>
      <input type="text" v-model='employee_name' name="employee_name" placeholder="Add Name" />
    </div>
    <div class="form-control">
      <label>Phone</label>
      <input type="text" v-model='phone' name="phone" placeholder="Add Phone" />
    </div>
    <div class="form-control">
      <label>Email</label>
      <input type="text" v-model='email' name="email" />
    </div>
    <div class="form-control">
      <label>Position</label>
      <input type="text" v-model='position' name="position" />
    </div>
    <input type="submit" value="Save" class="btn btn-block" />
  </form>
</template>

<script>
import axios from 'axios'

export default {
    name:'UpdateEmployee',
    props:{
      employees:Array
    },
    data(){
        return{
            employee_name: '',
            phone: '',
            email:'',
            position:'',
          }
    },
    methods:{

        onSubmit(e){
            e.preventDefault()

            if(!this.employee_name){
                alert('Please add employee')
                return 
            }
            const newEmployee = {
                employee_name:this.employee_name,
                phone:this.phone,
                email:this.email,
                position:this.position,
                
            }
            this.$emit('update-employee', newEmployee)
            this.employee_name='',
            this.phone= '',
            this.email= '',
            this.position= ''

        }
    },
    async mounted(){
      const res = await axios.get('api/employee/' + this.$route.params.id)
      this.employee = res.data
    },

    emits: ['update-employee',]
}
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 50%;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}

.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>