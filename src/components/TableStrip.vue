<template>  
 
    
      <th scope="row">{{user.id}}</th>
      <td>{{user.login}}</td>
      <td>
        <img :src="user.avatar_url" alt="avatar" width="200" height="200">
      </td>
    
</template>

<script>

export default {
  name: 'TableStrip',
  props: ['user'],
  components: {},
  methods: {

  }
}
</script>

<style scoped>



</style>
