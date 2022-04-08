<template>
  <Header/>
  
  <Employee @update-employee='updateEmployee' @show-employee='showEmployeeToggle' @delete-employee='deleteEmployee' :employee='employee' :showEmployee='showEmployee'/>
  
  <div class='main-box'>
  <AddEmployee v-show='showEmployee'  @add-employee='addEmployee' />
  <Footer/>
  </div>
    
  <br>



</template>

<script>
// @ is an alias to /src
import Header from '../components/Header'
import Button from '../components/Button'
import Employee from '../components/Employee'
import AddEmployee from '../components/AddEmployee'
import UpdateEmployee from '../components/UpdateEmployee'
import Footer from '../components/Footer'

export default {
  name: 'HomeView',
  components:{
    Header,
    Button,
    Employee,
    AddEmployee,
    UpdateEmployee,
    Footer
  },
  data(){
    return {
      employee:[],
      showEmployee: false
    }
  },
  methods:{
    updateEmployee(id){
      console.log(id)
    },
    showEmployeeToggle(){
      this.showEmployee = !this.showEmployee
    },
    async addEmployee(id){

      const res = await fetch('api/employee',{
        method: 'POST',
        headers: {
          'Content-type':'application/json',
          
        },
      body: JSON.stringify(id)
      })

      const data = await res.json()
      this.employee = [...this.employee,data]
    },
    async deleteEmployee(id){
      if (confirm('Are you sure?'))
      {
        const res = await fetch(`api/employee/${id}`,{
          method:'DELETE'
        })
        console.log(res)
        res.status === 200 ? (this.employee = this.employee.filter((employee) => employee.id !== id)) : alert('Error, Failed delete')

        }
    },
    async fetchEmployee(){
      const res = await fetch('api/employee')

      const data = await res.json()

      return data 
    },
    async fetchEmployeeUpdate(id){
      const res = await fetch(`api/employee/${id}`)

      const data = await res.json()

      return data 
  }, 
  }, 
  async created(){
    this.employee = await this.fetchEmployee()
  }
}
</script>
