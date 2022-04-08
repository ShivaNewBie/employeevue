<template>
    <!-- <UpdateEmployee @update-employee='updateEmployee'/> -->
    <div class='container' :key='member.id' v-for='member in employee'>
        <p>{{member.id}}</p>
        <p>{{member.employee_name}}</p>
        <p>{{member.phone}}</p>
        <p>{{member.email}}</p>
        <p>{{member.position}}</p>
        </div>
        <!-- {{employee}} --> 
    <br>

 
    <div class='container'><UpdateEmployee @update-employee='updateEmployee' :employee='employee'/></div>
    
</template>

<script>
import axios from 'axios'
import UpdateEmployee from '../components/UpdateEmployee'
import Employee from '../components/Employee'

export default {
    name: 'SpecificUser',
    components:{
        UpdateEmployee,
        Employee
    },
    data(){
    return {
      employee:[],
    }
      },
    
      
      mounted(){
          axios
          .get('api/employee/' + this.$route.params.id).then
          (response => (this.employee = response))

      },
        methods: {
 
        async updateEmployee(id){
        console.log(id)
        const res = await fetch(`api/employee/${id}`,{
        method: 'PUT',
        headers: {
          'Content-type':'application/json',
          
        },
      body: JSON.stringify(id)
      })
      const data = await res.json()
      
      this.employee = [this.employee,data]
      console.log(this.employee)
        },
        
    }

}
</script>

<style scoped>
.container {
    text-align: center;
    margin: auto;
    width: 50%;
}

</style>

