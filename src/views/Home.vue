<template>  
  <h1 class="text-center my-5">Home</h1>
  <div class="container text-center">
      <div class="spinner-border" v-if="loading === true" role="status">
          <span class="sr-only">Loading...</span>
      </div>
    <table class="table table-striped text-center" v-else>
  <thead>
    <tr>
      <th scope="col">S.No</th>
      <th scope="col">Full Name</th>
      <th scope="col">Image</th>
    </tr>
  </thead>
  <tbody>
        <tr v-for="(user, index) in users" :key=index>
          <TableStrip :user="user" />
        </tr>
      
  </tbody>
</table>
  </div>
</template>

<script>
  import TableStrip from './../components/TableStrip';
  import axios from 'axios';

export default {
  name: 'Home',
  data(){
    return{
      loading: true,
      users: []
    }
  },
  components: {TableStrip},
  mounted(){
   console.log('Mounted');
   axios.get('https://api.github.com/users').then(res=> {
     console.log('Data', res.data);
     this.users = res.data;
     this.loading = false;
   }).catch(err=> {
     this.loading = false;
     console.log('Error', err);
   })
  }
}
</script>

<style scoped>



</style>
