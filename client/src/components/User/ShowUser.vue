<template>
  <div class="user-card">
    <h1>Show User</h1>
    <div class="user-details">
      <p><span>ID:</span> {{ user.id }}</p>
      <p><span>Name:</span> {{ user.name }}</p>
      <p><span>Lastname:</span> {{ user.lastname }}</p>
      <p><span>Email:</span> {{ user.email }}</p>
      <p><span>Password:</span> {{ user.password }}</p>
      <p><span>Status:</span> {{ user.status }}</p>
      <p><span>Type:</span> {{ user.type }}</p>
      <p><span>Created At:</span> {{ user.createdAt }}</p>
    </div>
  </div>
</template>

<script>
import UsersService from "@/services/UsersService";

export default { 
  data(){
    return {
      user: {}
    }
  },
  async created() {
    try{
      var userId = this.$route.params.userId;
      this.user = (await UsersService.show(userId)).data;
    }catch(err){
      console.log(err);
    }
  }
}
</script>

<style scoped>
.user-card {
  background-color: #f9f9f9;
  border-radius: 10px;
  padding: 20px;
  max-width: 500px;
  margin: 20px auto;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  font-family: 'Arial', sans-serif;
}

h1 {
  text-align: center;
  color: #333;
  margin-bottom: 20px;
}

.user-details {
  padding: 10px;
}

.user-details p {
  font-size: 1.1em;
  color: #555;
  margin: 10px 0;
}

.user-details p span {
  font-weight: bold;
  color: #333;
  margin-right: 5px;
}

.user-details p:nth-child(odd) {
  background-color: #f1f1f1;
  border-radius: 5px;
  padding: 10px;
}

.user-details p:nth-child(even) {
  background-color: #ffffff;
  border-radius: 5px;
  padding: 10px;
}
</style>
