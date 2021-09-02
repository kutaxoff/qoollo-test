<template>
  <h1>Jobs</h1>
  <table>
      <tr>
          <th>Email</th>
          <th>Name</th>
          <th>Roles</th>
          <th>Last Login</th>
          <th></th>
      </tr>
      <tr v-for="user in users" :key="user.id">
        <td>
            <img :src="user.pic" :alt="user.id">
            {{ user.email }}
        </td>
        <td>
            {{ user.name }}
        </td>
        <td>
            <div v-for="role in user.Roles" :key="role">
                {{ role }}
            </div>
        </td>
        <td>
            {{ user.last_login }}
        </td>
        <td>
            <button @click="deleteUser(user)"> Delete </button>
        </td>
      </tr>
      
  </table>
  
</template>

<script>
export default {
  data() {
    return {
      users: [],
    }
  },
  mounted() {
    fetch('http://localhost:3000/users')
      .then(res => res.json())
      .then(data => this.users = data)
      .catch(err => console.log(err.message))
  },
  methods: {
      deleteUser(user){
          console.log("delete " + user.name)
      }
  }
}
</script>

<style>

</style>