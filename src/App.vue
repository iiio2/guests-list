<template>
  <div id="app">
      
      <h1 class="text-center heading">Guests List</h1>
      <guest-form></guest-form>  
   </div>
       
</template>

<script>
import GuestForm from "./components/GuestForm.vue"; 

export default {
  components:{
    GuestForm, 
  }  
}
</script>

<style>
  h1,h2,h3,h4,h5,h6,p,li,a{
    font-family: 'Noto Serif', serif;
  }
  .heading{
    padding:2rem 0; 
  }

</style>
