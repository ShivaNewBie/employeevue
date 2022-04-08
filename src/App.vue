
<template>

  <router-view/>
</template>

<script>


export default {
  name: 'App',


}

</script>

<style lang="scss">
body {
    font-family: 'Poppins', sans-serif;
    font-size: 14.4px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
h1 {
    color: red;
    padding: 15px 0 0 15px;
}
.main-box{
    margin: auto;
    width: 50%;
}

.content-table {
    border-collapse: collapse;
    border-left: 2px solid #009879;
    border-right: 2px solid #009879;
    border-radius: 5px 5px 0 0 ;
    overflow: hidden;
    box-shadow: 0 0 20px rgba(0,0,0,0.15);
}

.content-table thead tr{
    background-color: #009879;
    color: white;
    text-align: left;
    font-weight: bold;
}
.content-table th, .content-table td {
    padding: 12px 15px 12px 15px;
}

.content-table tbody tr{
    border-bottom: 1px solid #dddddd;
}
.content-table tbody tr:nth-of-type(even){
    background-color: #f3f3f3;
}
.content-table tbody tr:last-of-type{
    border-bottom:2px solid #009879
}

.update-box{
    max-width: 200px;
    height: 200px;
    border: 2px solid #009879;
    text-align: center;
    margin: 100px auto auto auto;

}

.button-1{
    height: 30px;
    font-family: 'Poppins', sans-serif;
    background-color: none;
    border:1px solid #dddddd;
}
.button-1:hover{
    background-color: #dddddd;
}
a {
    color: inherit;
    text-decoration: none;
}

a:hover{
    text-decoration: underline;
}


</style>
