<template>
           <div class='main-box'>
                <table class='content-table'>
                    <thead>
                        <tr>
                        <th>Name</th>
                        <th>Phone</th>
                        <th>Email</th>
                        <th>Position</th>
                        <th></th>
                        <th></th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr :key="member.id" v-for='member in employee'>
                            
                        <td>{{member.employee_name}}</td>
                        <td>{{member.phone}}</td>    
                        <td>{{member.email}}</td>    
                        <td>{{member.position}}</td>
                        <router-link :to="'' + member.id"><td><button @click='onUpdate(member.id)'>update</button></td></router-link>
                        <td><i @click='onDelete(member.id)' class='fas fa-times'></i></td>
                        </tr>
                    </tbody>
                </table>
                
    <br>
    <Button @btn-click="$emit('show-employee')"  :title="showEmployee ? 'Close':'Add Employee'" />

           </div>
</template>

<script>
import Button from './Button'

export default {
    name:'Employee',
    props:{
        employee:Array,
        showEmployee:Boolean
    },
    components:{
        Button,
    },
    methods: {
        onDelete(id){
            this.$emit('delete-employee',id)
        },
        onUpdate(id){
            this.$emit('click-employee',id)
            console.log(id)

        }
    },
    emits: ['delete-employee','show-employee','click-employee']
}
</script>

<style scoped>

.fas{
    color:red;
}
</style>